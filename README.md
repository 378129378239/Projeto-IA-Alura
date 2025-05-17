# Quantizador de Ações - App de Suporte para Lidar com Vícios (Assistido por IA)

Este projeto é um protótipo minimalista em Python de um aplicativo concebido para auxiliar usuários a quantificar e refletir sobre ações relacionadas a vícios ou hábitos que desejam superar. Ele utiliza a API Google Gemini para gerar perguntas personalizadas para um diário e fornecer feedbacks de apoio, baseando-se em informações de fontes confiáveis.

**Atenção:** Este é um protótipo para fins de demonstração e aprendizado. **Não é um substituto para aconselhamento, diagnóstico ou tratamento médico, psicológico ou terapêutico profissional.** Sempre procure o conselho de um profissional qualificado para quaisquer questões que possa ter sobre uma condição médica ou de saúde mental.

## Objetivos do Aplicativo

*   Oferecer uma ferramenta de auto-observação para que o usuário possa acompanhar a frequência e intensidade de um hábito/vício.
*   Fornecer perguntas reflexivas diárias geradas por IA para engajar o usuário.
*   Apresentar feedbacks mensais (gerados por IA) baseados nos relatos, oferecendo suporte, encorajamento e informações gerais.
*   Sugerir a busca por acompanhamento terapêutico profissional e fornecer informações básicas sobre abordagens psicológicas e onde buscar ajuda (CAPS, etc.).
*   Respeitar a privacidade do usuário, não coletando dados pessoais identificáveis diretamente e focando no tratamento de dados sensíveis com o devido cuidado, conforme a LGPD (simulado no protótipo).

## Principais Funcionalidades (Versão Protótipo em Python)

*   **Consentimento Informado:** Simula a coleta de consentimento do usuário antes do uso, informando sobre o tratamento de dados (incluindo o uso de IA) e a natureza sensível das informações, conforme a LGPD.
*   **ID de Usuário Anônimo:** Gera um ID único para simular a identificação do "dispositivo" sem coletar dados pessoais diretos.
*   **Configuração Inicial:**
    *   Usuário define o hábito/vício que deseja acompanhar.
    *   (Opcional) Usuário informa dados quantitativos sobre o hábito anterior para cálculo de economia (simulado).
    *   **Agente 1 (Formulador de Perguntas)** é chamado para criar perguntas personalizadas para o diário.
*   **Diário com Perguntas Geradas por IA:**
    *   O usuário responde diariamente a um conjunto de perguntas de "sim/não" formuladas pelo Agente 1.
    *   Registro da quantidade do hábito (se ocorrido).
*   **Feedback Personalizado com IA:**
    *   **Agente 2 (Gerador de Feedback)** analisa as respostas recentes do diário e o status do "streak" (sequência de dias sem o hábito).
    *   Gera mensagens de apoio, encorajamento e sugestões gerais de onde buscar informações, baseando-se nas URLs de referência.
    *   Inclui um cálculo simples de economia estimada.
*   **Informações sobre Terapias:** Apresenta uma lista de abordagens terapêuticas e sugere locais para buscar ajuda profissional.
*   **Streak de Dias:** Acompanha a sequência de dias em que o usuário relata não ter praticado o vício.
*   **Armazenamento Local de Dados:** Os dados do usuário (configuração, relatos, ID) são salvos em arquivos JSON locais (`quantizador_user_data.json` e `quantizador_user_id.txt`).
*   **Mensagens de Suporte e Recompensa (Simuladas):** O app exibe mensagens de encorajamento.

## Agentes de IA Utilizados (Simulados)

O aplicativo utiliza dois "agentes" conceituais que interagem com a API Google Gemini:

1.  **Agente 1: Formulador de Perguntas**
    *   **Responsabilidade:** Criar de 3 a 5 perguntas de Sim/Não para o diário do usuário.
    *   **Contexto:** Tipo de vício informado pelo usuário e um conjunto de URLs de referência sobre saúde mental, vícios e tipos de terapia.
    *   **Objetivo:** Gerar perguntas que incentivem a reflexão diária do usuário sobre seu hábito.

2.  **Agente 2: Gerador de Feedback**
    *   **Responsabilidade:** Criar mensagens de feedback personalizadas.
    *   **Contexto:** Tipo de vício, respostas recentes do diário do usuário, "streak" de dias e as URLs de referência.
    *   **Objetivo:** Oferecer suporte emocional, reconhecer esforços, sugerir fontes de informação confiáveis e reforçar a importância do acompanhamento profissional.

## Como Usar (Ambiente de Teste - Google Colab)

1.  **Configurar API Key:**
    *   Abra este notebook no Google Colab.
    *   No menu lateral esquerdo, clique no ícone de chave (🔑) chamado "Segredos".
    *   Adicione um novo secret com o nome `GOOGLE_API_KEY_GEMINI` e cole sua API Key do Google Gemini no campo "Valor".
    *   Certifique-se de que a opção "Acesso do notebook" está habilitada para este secret.

2.  **Instalar Bibliotecas:**
    *   Execute a seguinte célula no notebook para instalar a SDK do Google Gemini:
        ```python
        !pip install -q google-generativeai
        ```

3.  **Executar o Código Principal:**
    *   Cole o código Python fornecido (a "Versão 1: Código Python com Explicação Linha por Linha (Adaptado com Agentes)") em uma célula do Colab.
    *   Execute a célula.

4.  **Interação:**
    *   O aplicativo solicitará consentimento inicial. Digite `s` para concordar e continuar.
    *   Siga as instruções no console para configurar o hábito que deseja acompanhar e registrar seus relatos diários.
    *   Os arquivos `quantizador_user_data.json` e `quantizador_user_id.txt` serão criados no ambiente da sessão do Colab.

## Considerações Importantes (LGPD e Ética)

*   **Privacidade por Desenho (Privacy by Design):** Este protótipo simula boas práticas de privacidade, como o consentimento informado e a não coleta de dados pessoais diretos.
*   **Dados Sensíveis:** O aplicativo lida com informações sobre vícios, que são considerados dados pessoais sensíveis pela LGPD. O tratamento desses dados deve ser feito com extremo cuidado e segurança em um ambiente de produção.
*   **Transparência:** O usuário é informado sobre como seus dados (respostas anônimas ao diário) e o tipo de vício serão usados pela IA para gerar perguntas e feedbacks.
*   **Minimização de Dados:** Apenas os dados essenciais para as funcionalidades descritas são solicitados.
*   **Segurança dos Dados:** No protótipo, os dados são armazenados localmente em arquivos JSON. **Em um aplicativo real, seriam necessárias medidas de segurança robustas**, como criptografia de dados em repouso e em trânsito, e armazenamento seguro (preferencialmente local no dispositivo do usuário, se possível, ou em servidores seguros com políticas rígidas de acesso e anonimização/pseudoanonimização).
*   **Fontes de Informação para IA:** Os agentes foram instruídos a basear suas respostas nas URLs fornecidas, que são de fontes consideradas confiáveis (órgãos governamentais, organizações de saúde).
*   **Limitações da IA:** É importante lembrar que a IA pode gerar informações incorretas ou incompletas. Os feedbacks e perguntas são ferramentas de suporte e reflexão, não devendo ser considerados como aconselhamento profissional definitivo.

## Tecnologias Utilizadas (Protótipo)

*   Python 3
*   Google Gemini API (via SDK `google-generativeai`)
*   Bibliotecas padrão do Python: `json`, `os`, `datetime`, `uuid`

## Próximos Passos / Melhorias Futuras

*   Desenvolvimento de uma interface gráfica para Android (ex: com Kivy, React Native, Flutter ou nativo Java/Kotlin).
*   Implementação de um sistema de banco de dados local seguro (SQLite) ou, se necessário, em nuvem com criptografia forte.
*   Mecanismos reais de identificação de dispositivo (respeitando a privacidade do usuário).
*   Notificações push reais e personalizáveis.
*   Gráficos e visualizações de progresso para o usuário.
*   Maior personalização das recompensas e sugestões de atividades.
*   Implementação de técnicas de RAG (Retrieval Augmented Generation) para um uso mais eficiente e preciso do conteúdo das URLs pelos agentes de IA.
*   Testes extensivos com usuários para refinar a usabilidade e a eficácia das perguntas e feedbacks.
*   Consultoria jurídica especializada para garantir total conformidade com a LGPD e outras regulamentações antes de qualquer lançamento.

---
