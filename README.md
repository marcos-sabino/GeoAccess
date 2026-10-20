Markdown
# 🗺️ GeoAccess — Navegação Inteligente e Acessibilidade Urbana

> Projeto acadêmico desenvolvido para a disciplina de **Engenharia de Software I** do 1º Semestre — **FATEC**.

---

## 📌 1. Sobre o Projeto

### 1.1 Breve Descrição
O **GeoAccess** é uma plataforma de navegação por mapas e rotas (estilo Google Maps e Waze) focada em **mobilidade urbana, acessibilidade e inteligência comunitária**. 

Além de oferecer as funcionalidades tradicionais de GPS, busca de locais e cálculo de rotas otimizadas para motoristas e pedestres, o **GeoAccess** permite que a comunidade mapeie e reporte em tempo real as condições de acessibilidade das vias públicas (presença de rampas, calçadas esburacadas, elevadores fora de serviço em estações, travessias seguras e iluminação pública).

### 🎯 Problema e Solução
* **Problema:** Pessoas com mobilidade reduzida, cadeirantes, idosos e pais com carrinhos de bebê enfrentam imensas dificuldades de deslocamento urbano, pois os mapas tradicionais não informam sobre a qualidade das calçadas e a acessibilidade dos caminhos.
* **Solução:** Um sistema de mapas colaborativo que calcula a "Rota Acessível" ideal com base nas necessidades específicas do usuário e nos alertas enviados em tempo real pela própria comunidade.

---

## 🛠️ 2. Tecnologias, Ferramentas e Infraestrutura

A arquitetura do projeto foi planejada para suportar renderização rápida de mapas, geolocalização precisa e processamento de dados espaciais em alta escala:

| Camada / Módulo | Tecnologia / Ferramenta | Descrição e Finalidade |
| :--- | :--- | :--- |
| **Mobile App (Frontend)** | React Native + TypeScript | Aplicativo multiplataforma (Android/iOS) para navegação GPS e alertas. |
| **Renderização de Mapas** | Mapbox GL SDK / Leaflet | Engine gráfica para renderização fluida de mapas vetoriais 2D/3D. |
| **Web Dashboard** | React.js + Tailwind CSS | Painel web para gestão de relatórios urbanos e moderação da comunidade. |
| **Backend API** | Node.js (NestJS) | API RESTful responsável pela lógica de rotas, usuários e alertas. |
| **Banco de Dados Espacial**| PostgreSQL + PostGIS | Banco de dados relacional com extensão geográfica para cálculo de rotas e coordenadas. |
| **Cache & Real-time** | Redis + WebSockets | Gerenciamento de sessões e envio de alertas de trânsito/vias em tempo real. |
| **Infraestrutura Cloud** | AWS (EC2, S3, RDS) | Hospedagem da API, banco geográfico na nuvem e armazenamento de fotos de alertas. |
| **Prototipagem & UX** | Figma | Design das telas, fluxo de navegação e protótipo interativo. |

---

## 🔄 3. Metodologias Utilizadas

### 📐 3.1 Modelo de Desenvolvimento: **Modelo Espiral**
Para este projeto, optou-se pelo **Modelo Espiral** (de Barry Boehm) em vez do modelo Cascata.

**Por que o Espiral?**
1. **Análise e Mitigação de Riscos:** Projetos baseados em mapas envolvem alto risco técnico no consumo de APIs geográficas, precisão do GPS e latência de rede. O modelo espiral permite avaliar e mitigar esses riscos a cada ciclo.
2. **Evolução Iterativa:** A aplicação evolui por meio de protótipos funcionais sucessivos (Ciclo 1: Busca e renderização do mapa; Ciclo 2: Roteamento simples; Ciclo 3: Alertas comunitários e rotas acessíveis).

      [1. Determinar Objetivos]
                 |
[4. Planejar] <----+----> [2. Identificar e Resolver Riscos]
|
[3. Desenvolver e Testar Protótipos]


---

### 🔀 3.2 Estratégia de Versionamento: **Git & GitFlow**
Utilizamos o controle de versão com **Git** e a plataforma **GitHub**, adotando a convenção de ramificação **GitFlow**:

* `main`: Branch estritamente estável com o código em produção.
* `develop`: Branch de integração de todas as novas funcionalidades testadas.
* `feature/nome-da-feature`: Branches temporárias criadas a partir de `develop` para desenvolvimento de telas ou módulos específicos (ex: `feature/busca-enderecos`, `feature/alerta-obstaculo`).
* `hotfix/nome-do-bug`: Branches urgentes para correção direta de erros críticos detectados em produção.

**Exemplo de fluxo de comandos utilizado pela equipe:**
```bash
# Criando uma nova funcionalidade
git checkout develop
git checkout -b feature/rota-acessivel

# Salvando alterações e enviando ao GitHub
git add .
git commit -m "feat: implementa algoritmo de cálculo de rota com rampa"
git push origin feature/rota-acessivel
```
🖥️ 4. Projeto de Interface (UI/UX)
Abaixo estão os esboços conceituais do fluxo principal do aplicativo mobile do GeoAccess:

📱 Módulos e Fluxo de Telas (Wireframe)
```
+---------------------------+    +---------------------------+    +---------------------------+
| [🔍 Digite seu destino ]  |    | [🗺️ MAPA / ROTA ATIVA]    |    | [⚠️ REPORTAR OBSTÁCULO]   |
|                           |    |                           |    |                           |
|  PERFIL DE MOBILIDADE:    |    |   +-------------------+   |    | Tipo de Alerta:           |
|  (x) Cadeirante / Rampa   |    |   | 🚶 Rota Acessível |   |    | ( ) Calçada esburacada    |
|  ( ) Pedestre Padrão      |    |   | ⏱️ 12 min (850m)  |   |    | (x) Degrau sem rampa      |
|  ( ) Ciclovia             |    |   +-------------------+   |    | ( ) Obras na via          |
|                           |    |                           |    |                           |
|  HISTÓRICO RECENTE:       |    |   [ ⚠️ Obstáculo a 100m ] |    | [📷 Adicionar Foto]       |
|  📍 Estação Central       |    |   [ 🔊 Iniciar Rota ]     |    |                           |
|  📍 Parque da Cidade      |    |                           |    | [ ENVIAR ALERTA ]         |
+---------------------------+    +---------------------------+    +---------------------------+
```
   1. Busca e Opções de Rota          2. Navegação em Tempo Real           3. Reportar Alerta
👥 Autor
Desenvolvido por Marcos Sabino

Estudante de Bigdate / Engenharia de Software — FATEC.

GitHub: @marcos-sabino
