# MDA - Mozambican Digital Architecture

## Visão

A Arquitetura Digital Moçambicana (MDA) é uma iniciativa nacional liderada pelo Partido ACORDAMOS para criar uma infraestrutura digital governamental modular, aberta e de código livre. a MDA fornece um plano de referência para a construção de sistemas interoperáveis, seguros e extensíveis para a administração pública.

A MDA tem como objetivo capacitar desenvolvedores, instituições e cidadãos a modernizar a governação com transparência, responsabilidade e excelência técnica.

---

## Filosofia e Princípios Fundamentais

1. **Aberto por Definição**

   * Todo o software, API e padrão é de código aberto e publicamente documentado.

2. **Design Centrado no Cidadão**

   * Interfaces e fluxos desenhados para máxima usabilidade e inclusão.

3. **Modular e Extensível**

   * Cada componente funciona de forma independente, mas comunica com os demais.

4. **Infraestrutura Offline-First**

   * Projetada para funcionar mesmo em zonas sem conectividade contínua.

5. **Governança Transparente**

   * Backlog público, commits rastreáveis e entregas verificáveis.

---

## Estrutura Arquitetural

### 1. **Camada de Serviços Públicos Digitais**

Interface direta com o cidadão.

#### Subsistemas Principais:

* **Hospital+** – Registos clínicos, logística hospitalar, gestão de inventário
* **Escola+** – Gestão escolar: alunos, turmas, exames, frequência
* **ID.MZ** – Registo civil e emissão de documentos de identidade
* **Logística Pública** – Transporte público, rastreamento de frotas e carga
* **SIGEF+** – Recursos humanos e folha de pagamentos dos funcionários públicos

---

### 2. **APIs Intersetoriais do Estado**

Camada de serviços que conecta os diversos sectores governamentais.

#### Funcionalidades:

* APIs REST/gRPC padronizadas
* Autenticação via OAuth2 / OIDC
* Gateway de APIs com versionamento e observabilidade
* Webhooks para eventos interdepartamentais em tempo real

#### Exemplos de Endpoints:

* `/api/identidade/verificar`
* `/api/educacao/boletim`
* `/api/saude/imunizacao`
* `/api/logistica/localizacao`

---

### 3. **Serviços Centrais da Plataforma**

Serviços partilhados entre todas as aplicações.

#### Componentes:

* **Portal de Autenticação** – Gestão centralizada de identidade e permissões
* **Hub de Notificações** – Envio de SMS, email, USSD e push
* **Cofre de Arquivos** – Armazenamento encriptado de documentos
* **Módulo de Auditoria** – Registo completo de ações dos utilizadores e sistemas
* **Sistema Nacional de Design** – Biblioteca de componentes frontend reutilizáveis

---

### 4. **Camada de Dados e Análises**

* **Lago Nacional de Dados** com agregações anónimas
* **Dashboards Públicos** com Kibana/Grafana
* **ETLs dos subsistemas MDA**
* **Portal de Dados Abertos** para jornalistas, ONGs e pesquisadores

---

### 5. **Governação e Desenvolvimento**

* **Backlog Público** – Acompanhamento dos responsáveis, atrasos e progresso
* **Pipelines CI/CD** – Entregas contínuas com versionamento público
* **Revisão Técnica de Código** – Checklist de segurança, acessibilidade e lógica
* **Governança Modular** – Equipes provinciais e sectoriais podem gerir verticalmente

---

## Domínios Sectoriais

### ⚕️ Saúde

* Registos médicos eletrónicos
* Cadastro nacional de vacinação
* Gestão de cadeias logísticas hospitalares

### 🏫 Educação

* Registos de desempenho escolar
* Planeamento de infraestruturas
* Gestão descentralizada de escolas

### 🚴 Mobilidade e Logística

* Rastreamento em tempo real do transporte público
* Licenciamento digital de veículos e condutores

### 🏢 Administração Pública

* Recrutamento e folha de pagamento
* Controle de assiduidade e disciplina funcional

### 💳 Finanças Públicas

* Painéis orçamentais, compras públicas e execução financeira

### 🌍 Identidade Nacional

* Nascimentos, óbitos, casamentos
* Emissão e verificação de documentos oficiais

### ⛨️ Segurança, Justiça e Integridade

* **Sistema Nacional de Denúncias** – Plataforma anónima e rastreável para denúncia de corrupção, abusos e crimes administrativos
* **Módulo de Inteligência** – Apoio à segurança pública com análise preditiva de risco
* **Antifraude** – Sistemas de verificação cruzada e detecção de anomalias em tempo real
* **Registo de Incidentes** – Integração com forças de segurança e linhas de emergência
* **Painel Anti-Corrupção** – Visualização pública de processos, investigações e resultados

---

## Licenciamento

Todos os sistemas são distribuídos sob a licença **GNU AGPL v3**, garantindo que o código público permaneça público.

---

## Como Contribuir

Junta-te à nossa organização no GitHub:

* [https://github.com/acordamos](https://github.com/acordamos)

Contribui com código, ideias, documentação ou revisão técnica. A MDA é o início de uma transformação nacional — **em código**.

> *"Pedra a pedra, compilamos um novo Estado."*
