# Avali-e 📊

<div align="center">

![Avali-e Logo](./frontend-web/src/assets/logo.png)

**Sistema completo de gestão e avaliação acadêmica para instituições de ensino**

[![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://www.java.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Kotlin](https://img.shields.io/badge/Kotlin-0095D5?style=for-the-badge&logo=kotlin&logoColor=white)](https://kotlinlang.org/)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)](https://spring.io/projects/spring-boot)

</div>

## 📋 Sobre o Projeto

O **Avali-e** é um sistema fullstack completo desenvolvido para facilitar a gestão e coleta de avaliações acadêmicas em instituições de ensino. O sistema permite que professores solicitem feedbacks de seus alunos, diretores gerenciem professores e disciplinas, e alunos forneçam avaliações através de uma interface web ou aplicativo móvel.

### ✨ Principais Funcionalidades

- 🔐 **Sistema de Autenticação**: Login seguro com JWT (Access Token e Refresh Token)
- 👥 **Gestão de Usuários**: Gerenciamento de alunos, professores e diretores
- 📚 **Gestão de Disciplinas**: Controle de disciplinas, horários e turmas
- 📝 **Solicitação de Avaliações**: Professores podem solicitar feedbacks de forma automatizada
- ⭐ **Sistema de Avaliação**: Alunos avaliam professores com notas e comentários
- 📊 **Dashboard Analítico**: Visualização de estatísticas e últimas avaliações
- 🔍 **Filtragem Avançada**: Filtros por disciplina, data, nota e período
- 📱 **Multiplataforma**: Acesso via web e aplicativo móvel Android
- 📧 **Notificações por Email**: Envio automático de solicitações de avaliação

## 🏗️ Arquitetura

O projeto segue uma arquitetura monorepo dividida em três aplicações principais:

```
fullstack-avali-e/
├── backend/              # API REST com Spring Boot
├── frontend-web/         # Aplicação web com React + TypeScript
└── frontend-mobile/      # Aplicativo Android nativo com Kotlin
```

### 🔧 Stack Tecnológica

#### Backend
- **Framework**: Spring Boot
- **Linguagem**: Java
- **Banco de Dados**:  MongoDB
- **Autenticação**:  Spring Security + JWT
- **Validação**:  Bean Validation
- **Email**: Spring Mail

#### Frontend Web
- **Framework**: React 18
- **Linguagem**: TypeScript
- **Build Tool**: Vite
- **Styling**: Tailwind CSS
- **Roteamento**: React Router v6
- **HTTP Client**: Fetch API
- **UI Components**: Lucide Icons
- **Notificações**:  Sonner
- **Date Handling**: date-fns

#### Frontend Mobile
- **Plataforma**: Android
- **Linguagem**:  Kotlin
- **Build System**: Gradle
- **HTTP Client**: OkHttp
- **Coroutines**: Kotlin Coroutines

## 🚀 Como Executar

### Pré-requisitos

- **Java** 17 ou superior
- **Node.js** 18 ou superior
- **MongoDB** 4.4 ou superior
- **Android Studio** (para o mobile)
- **npm** ou **yarn**

### 🗄️ Configuração do Banco de Dados

1.  Instale e inicie o MongoDB:
```bash
# MongoDB deve estar rodando na porta padrão 27017
mongod
```

2. O banco de dados será criado automaticamente na primeira execução

### 🖥️ Backend

1. Navegue até o diretório do backend:
```bash
cd backend
```

2. Configure as variáveis de ambiente no `application.properties` ou `application.yml`:
```properties
# MongoDB
spring.data.mongodb.uri=mongodb://localhost:27017/avalie

# JWT
jwt.secret=your-secret-key
jwt.expiration. access=3600000
jwt.expiration.refresh=86400000

# Email (configure com suas credenciais)
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=your-email@gmail.com
spring.mail.password=your-app-password
```

3. Execute a aplicação:
```bash
# Com Maven
./mvnw spring-boot:run

# Com Gradle
./gradlew bootRun
```

O backend estará disponível em `http://localhost:8080`

### 🌐 Frontend Web

1. Navegue até o diretório do frontend:
```bash
cd frontend-web
```

2. Instale as dependências:
```bash
npm install
```

3. Configure a variável de ambiente criando um arquivo `.env`:
```env
VITE_API_URL=http://localhost:8080
```

4. Execute em modo de desenvolvimento:
```bash
npm run dev
```

A aplicação estará disponível em `http://localhost:3000`

5. Para build de produção:
```bash
npm run build
```

### 📱 Frontend Mobile

1. Abra o projeto no Android Studio: 
```bash
cd frontend-mobile
```

2. Aguarde a sincronização do Gradle

3. Configure a URL da API no arquivo de configuração ou diretamente no código:
```kotlin
// Em MainActivity.kt ou onde a URL é definida
val API_URL = "http://10.0.2.2:8080" // Para emulador
// val API_URL = "http://SEU_IP:8080" // Para dispositivo físico
```

4. Execute no emulador ou dispositivo físico

## 📚 Documentação da API

### Endpoints Principais

#### Autenticação
```
POST /login                 - Autenticação de usuário
POST /refresh               - Renovação do token de acesso
```

#### Alunos
```
GET    /student/findAll               - Lista todos os alunos
GET    /student/findById? id={id}      - Busca aluno por ID
POST   /student/register              - Cadastra novo aluno
PUT    /student/update?id={id}        - Atualiza aluno
DELETE /student/delete?id={id}        - Remove aluno
```

#### Professores
```
GET    /professor/findAll             - Lista todos os professores
GET    /professor/findById?id={id}    - Busca professor por ID
POST   /professor/register            - Cadastra novo professor
PUT    /professor/update?id={id}      - Atualiza professor
DELETE /professor/delete?id={id}      - Remove professor
```

#### Diretores
```
GET    /director/findAll              - Lista todos os diretores
GET    /director/findById? id={id}     - Busca diretor por ID
POST   /director/register             - Cadastra novo diretor
PUT    /director/update?id={id}       - Atualiza diretor
DELETE /director/delete?id={id}       - Remove diretor
```

#### Disciplinas
```
GET    /disciplines/findAll                    - Lista todas as disciplinas
GET    /disciplines/findById?id={id}           - Busca disciplina por ID
POST   /disciplines/register                   - Cadastra nova disciplina
PUT    /disciplines/update?id={id}             - Atualiza disciplina
DELETE /disciplines/delete?id={id}             - Remove disciplina
```

#### Feedbacks
```
GET  /feedback/findAll                        - Lista todos os feedbacks
GET  /feedback/findByStudent?studentId={id}   - Feedbacks por aluno
GET  /feedback/findByDiscipline?disciplineId={id} - Feedbacks por disciplina
GET  /feedback/findByNote?note={note}         - Feedbacks por nota
POST /feedback/register                       - Registra novo feedback
```

#### Email
```
POST /email/sendFeedback? disciplineId={id}   - Envia solicitação de avaliação
```

### Exemplo de Request Body

#### Login
```json
{
  "email": "usuario@example.com",
  "password": "senha123"
}
```

#### Registro de Feedback
```json
{
  "text": "Excelente professor, aulas dinâmicas",
  "student": "64abc123def456789",
  "discipline": "64xyz789abc123456",
  "note": 5,
  "date": "2024-01-15T10:30:00Z"
}
```

## 👥 Níveis de Acesso

O sistema possui três níveis de acesso hierárquicos:

| Nível | Usuário | Permissões |
|-------|---------|------------|
| 0 | Aluno | Visualizar feedbacks próprios, enviar avaliações |
| 1 | Professor | Todas as permissões de aluno + solicitar avaliações, visualizar dashboard |
| 2 | Diretor | Todas as permissões de professor + gerenciar professores, visualizar relatórios completos |

## 🎨 Funcionalidades por Interface

### Interface Web (Professores e Diretores)

- **Dashboard**: Estatísticas e visualização de últimas avaliações
- **Solicitar Avaliação**: Envio de solicitações para alunos de uma disciplina
- **Feedbacks**: Visualização e filtragem de todas as avaliações recebidas
- **Professores**: Gerenciamento de professores (apenas diretores)
- **Perfil**: Atualização de dados pessoais e senha

### Interface Mobile (Alunos)

- **Login**: Acesso seguro ao sistema
- **Avaliação**: Interface simples para avaliar professores
- **Deep Link**: Acesso direto via link recebido por email

## 🔒 Segurança

- ✅ Autenticação JWT com tokens de acesso e renovação
- ✅ Senhas criptografadas com BCrypt
- ✅ Controle de acesso baseado em níveis
- ✅ Rotas protegidas no frontend e backend
- ✅ Validação de dados no lado do servidor
- ✅ Renovação automática de tokens

## 🤝 Contribuindo

Contribuições são bem-vindas! Para contribuir: 

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto é privado e está sob propriedade de seus desenvolvedores.

## 👨‍💻 Desenvolvedor

**Breno Crepaldi**

- GitHub: [@brenocrepaldi](https://github.com/brenocrepaldi)
- LinkedIn: [Breno Crepaldi](https://linkedin.com/in/brenocrepaldi)

---

<div align="center">
Desenvolvido com ❤️ para facilitar a gestão educacional
</div>
