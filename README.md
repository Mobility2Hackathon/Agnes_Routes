# 🛡️ Agnes Routes

**Projeto desenvolvido durante hackathon do Instituto Joule.**  
O Agnes Routes propõe uma solução com Inteligência Artificial para segurança de mulheres na mobilidade urbana, utilizando dados territoriais, infraestrutura, percepção emocional e análise de risco para sugerir rotas mais seguras.

---

## 📌 Sobre o Projeto

O Agnes Routes é uma solução tecnológica voltada para a segurança de mulheres em seus deslocamentos urbanos.  
O nome homenageia Agnes Meyer Driscoll, criptologista americana pioneira em segurança da informação.  
Essa escolha reforça o propósito central do projeto: utilizar tecnologia, dados e inteligência artificial para ampliar a proteção e o direito de ir e vir das mulheres nas cidades.

---

## 🚨 Problema e Contexto Histórico

O projeto parte da identificação de que a insegurança no deslocamento diário é uma dificuldade central enfrentada pelas mulheres, manifestada por assédio, violência e sensação constante de medo.  
Isso leva muitas a alterar rotinas e trajetos, impactando sua liberdade e qualidade de vida.

### Hipótese / Insight Central

A hipótese foi validada através de reportagens e de uma pesquisa própria realizada com 50 mulheres.

- Os relatos coletados evidenciaram que todas as participantes já sofreram ou presenciaram algum tipo de violência no deslocamento urbano.
- A decisão de rota é fortemente guiada pelo medo e pela experiência vivida.
- O principal insight é a ausência de uma ferramenta que combine dados reais do território urbano (infraestrutura) com experiências emocionais e comportamentais reais (dados primários).

---

## 🎤 Entrevista com Especialista em Dados e IA

### Midian Brandão  
https://www.linkedin.com/in/midian-brandao/

A arquitetura do modelo de risco foi validada e aprimorada pela profissional de dados e IA, Midian Brandão.  
Sua análise confirmou a necessidade de uma IA situacional e centrada na experiência da mulher:

- **Validação da Ponderação:**  
  Midian destacou que o fator mais negligenciado, mas que mais pesa na segurança prática, é o estado real da rua (iluminação fraca, calçada quebrada, canto escuro, ponto cego). Isso justificou o alto peso dado ao índice de iluminação no modelo final.

- **Reatividade em Tempo Real:**  
  A especialista sugeriu que, para ser realmente útil, a solução deveria dividir a atualização dos dados em três ciclos (Clocks de Risco):
  - Hot (5–10 segundos)  
  - Warm (1–3 horas)  
  - Cold (6–24 horas)

- **Dica para Viabilidade:**  
  Uso de APIs externas como Google Maps Directions & Roads API e OpenStreetMap + Overpass API.

- **Geração de Alerta Tático:**  
  Combo Visual claro (mapa em vermelho), alerta rápido ("Trecho arriscado agora") e solução imediata (sugestão de rota mais segura automaticamente).

---

## 📱 Descrição da Solução e Fluxo Básico de Uso (MVP)

O Agnes Routes é um aplicativo móvel que sugere rotas mais seguras, e não apenas mais rápidas.

### Fluxo Básico de Uso

1. **Acesso e Cadastro:** Usuária faz login e, obrigatoriamente, cadastra dois Contatos de Emergência.  
2. **Busca de Destino:** A usuária seleciona um destino e o aplicativo inicia a simulação.  
3. **Cálculo da Rota Segura:** Mensagem exibida: *"Calculando rota mais segura..."*.  
4. **Visualização do Risco e Rota:** Exibição de Zonas de Risco, Comércios Próximos e Opções de Transporte.

### Entrega do MVP (Desenvolvimento Figma)

O MVP entrega:

- Telas Essenciais: Login, Cadastro, Perfil, Rotas Salvas e Configurações.  
- Funções de Emergência: Compartilhamento de localização em tempo real e chamada de emergência.  
- Interação Colaborativa: Relatos de insegurança em pontos do mapa.  
- Simulação de Roteamento respeitando vias urbanas.

🔗 **Link para acesso ao modelo Figma:**  
http://bit.ly/48QPymW

---

## 🤖 Uso da Inteligência Artificial na Solução

A IA atua na qualificação do território urbano (Scoring Territorial).

### Modelo de Scoring Ponderado

| Índice | Peso | Funções da IA |
|------|------|---------------|
| Baixa Iluminação (dark_index) | 40% | Mede densidade e espaçamento de luzes |
| Fluxo de Pessoas (flux_index) | 30% | Penaliza ruas desertas |
| Infraestrutura Urbana (infra_index) | 15% | Avalia vias e acesso |
| Percepção Emocional (emocional_index) | 15% | Modelado a partir de relatos reais |

O Índice de Risco Final varia de **0 a 100**.

---

## ⚖️ Uso Ético e Responsável da IA

- Transparência e Explicabilidade  
- Privacidade e Anonimato  
- Mitigação de Viés  
- Foco na Prevenção, Não na Vigilância  

---

## 💼 Modelo de Negócio e Monetização

O Agnes Routes adota um modelo de negócios Business-to-Government (B2G), baseado em serviços e licitação pública: 

Licitação e Segurança Pública: O aplicativo visa atender a uma licitação de projeto solicitada pela Secretaria de Segurança Pública de São Paulo (SSP-SP). A monetização ocorre através da contratação do serviço pelo órgão público para garantir a segurança da mulher, fornecendo uma solução de prevenção de riscos com IA para uso da população. 

Benefício Público: O foco é na otimização dos recursos de segurança pública, oferecendo uma camada preditiva e prescritiva que reduz a exposição ao risco e fornece dados valiosos para o planejamento urbano e policial (Ex: onde instalar mais iluminação, onde concentrar patrulhamento em horários críticos).

---

## 📂 Estrutura do Projeto

```bash
hackathon_dados/
│
├── base_geosampa_distritos/
│   └── geoportal_distrito_municipal_v2.geojson
│
├── bases_geosampa_criminalidade/
│   ├── geoportal_equipamento_guarda_civil_metropolitana_v2.geojson
│   ├── geoportal_equipamento_policia_civil_v2.geojson
│   └── geoportal_equipamento_policia_militar_v2.geojson
│
├── bases_geosampa_iluminacao_mobilidade/
│   ├── SIRGAS_SHP_iluminacaopublica/
│   │   ├── .cpg .dbf .shp .shx
│   ├── SIRGAS_SHP_quadraviariaed_2017/
│   │   ├── .cpg .dbf .shp .shx
│   ├── geoportal_equipamento_shopping_center.geojson
│   ├── geoportal_estacao_metro_v2.geojson
│   ├── geoportal_estacao_trem_v2.geojson
│   └── geoportal_ponto_onibus.geojson
│
├── bases_sinesp_criminalidade/
│   ├── BancoVDE 2021.xlsx
│   ├── BancoVDE 2022.xlsx
│   ├── BancoVDE 2023.xlsx
│   └── BancoVDE 2024.xlsx
│
└── bases_ssp_criminalidade/
    ├── OcorrenciaMensal(Criminal)-São Paulo.xlsx
▶️ Como Executar o Notebook de Análise
1️⃣ Baixar o Projeto

Clique em Code

Selecione Download ZIP

Extraia a pasta em seu computador

2️⃣ Preparar o Ambiente
pip install pandas geopandas matplotlib numpy jupyter

3️⃣ Executar o Notebook
jupyter notebook


Abra o notebook presente na pasta do projeto

Execute as células em ordem para reproduzir as análises

🚀 Considerações Finais

Este repositório apresenta a base analítica e conceitual do Agnes Routes, incluindo dados,
modelagem de risco e validação da proposta como MVP de impacto social com uso responsável de Inteligência Artificial.
