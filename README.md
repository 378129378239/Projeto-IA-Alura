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

## Fontes

## Esse foi um resumo das pesquisas que fiz no https://notebooklm.google.com/ para alimentar o https://aistudio.google.com/app/prompts/new_chat?utm_source=website&utm_medium=referral&utm_campaign=Alura-may-25 e assim criar os prompts para o https://colab.research.google.com/ https://aistudio.google.com/app/prompts?state=%7B%22ids%22:%5B%221E7yah0Hor-V08V-X1wuh2IRVopBTtymK%22%5D,%22action%22:%22open%22,%22userId%22:%22106405745783266077759%22,%22resourceKeys%22:%7B%7D%7D&usp=sharing, https://drive.google.com/file/d/1E9qx281_cWuLHPuNRYpHBWn1eQ-dg6dL/view?usp=sharing, https://drive.google.com/file/d/1ze6q5FRjgHvvlrI_xTAVWnGsGFyrUsNL/view?usp=sharing

Segue:

*   **"ARTIGOS - O Poder Judiciário nas constituições do Brasil - CNJ"**: Este material contém referências e links para diversos documentos históricos e artigos sobre o Poder Judiciário no Brasil. Os links específicos fornecidos nos excertos incluem:
    *   Ato Institucional nº 2, de 27 de outubro de 1965: <http://www.planalto.gov.br/ccivil_03/AIT/ ait-02-65.htm>
    *   Ato Institucional nº 5, de 13 de dezembro de 1968: <http://www.planalto.gov.br/ ccivil_03/AIT/ait-05-68.htm>
    *   Constituição Política do Império do Brasil, 1824: <http://www.planalto.gov.br/ ccivil_03/constituicao/constituicao24.htm>
    *   Emenda Constitucional nº 11, 1978: <http://www.planalto.gov.br/ccivil_03/constituicao/ emendas/emc_anterior1988/emc11-78.htm>
    *   Lei nº 4.898, de 9 de dezembro de 1965: <http://www.planalto.gov.br/ccivil_03/leis/ L4898.htm>
    *   Lei nº 4.717, de 29 de junho de 1965: <http://www.planalto.gov.br/ccivil_03/LeIs/L4717. htm>
    *   Lei Complementar nº 35, de 14 de março de 1979: <http://www.planalto.gov.br/ ccivil_03/leis/lcp/lcp35.htm>
    *   Discurso do Presidente Ernesto Geisel, 1º abr. 1977: <http://www.biblioteca.presidencia.gov.br/ ex-presidentes/ernesto-geisel/discursos-1/1977/15.pdf/ at_download/file>
    *   Artigo "Inconveniência e Inutilidade do Aumento dos Ministros do Supremo Tribunal Federal" de Álvaro Moutinho Ribeiro da Costa: <http://www.stf. jus.br/arquivo/biblioteca/PastasMinistros/RibeiroCosta/ ArtigosJornais/1965_out_20.pdf>
    *   Artigo "Evolução Histórica da Estrutura Judiciária Brasileira" de Ives Gandra da Silva Martins Filho: <http://www. planalto.gov.br/ccivil_03/revista/Rev_05/evol_historica. htm>
    *   "Notas sobre o Supremo Tribunal (Império e República)" de José Celso de Mello Filho: <http://www.stf.jus.br/arquivo/cms/ publicacaoPublicacaoInstitucionalCuriosidade/anexo/ Notas_informativas_sobre_o_STF_versao_de_2012.pdf>

*   **"Como ajudar uma pessoa DepeNDeNTe De Drogas - Portal Gov.br"**: Esta cartilha, associada ao Portal Gov.br, tem como título "Como ajudar uma pessoa DepeNDeNTe De Drogas". Embora não haja um link direto para o documento nos trechos, ele menciona a disponibilidade de um aplicativo (Zappar) para acesso a conteúdos extras através de códigos de Realidade Aumentada, com links para download no Google Play e App Store indicados por QR codes.

*   **"Constituição Federal: o que é e qual a importância? Confira! - Gran Faculdade"**: O título deste artigo da Gran Faculdade é "Constituição Federal: o que é e qual a importância? Confira!". Os trechos fornecidos focam na estrutura do site e nos tópicos abordados no artigo, mas não incluem um link direto para o conteúdo completo.

*   **"Constituição da República Federativa do Brasil - Senado Federal"**: Esta fonte apresenta trechos da Constituição da República Federativa do Brasil, bem como da Convenção sobre os Direitos das Pessoas com Deficiência e seu Protocolo Facultativo, e um índice temático. Não há um link único direto para a versão completa do documento nos excertos.

*   **"MI-mhGAP Manual de Intervenções para transtornos mentais, neurológicos e por uso de álcool e outras - Iris Paho"**: O título completo deste manual é "MI-mhGAP Manual de Intervenções para transtornos mentais, neurológicos e por uso de álcool e outras drogas na rede de atenção básica à saúde. Versão 2.0". Um link para os dados de catalogação está disponível: <http://iris.paho.org>.

*   **"Marco Civil da Internet – Wikipédia, a enciclopédia livre"**: Este é um artigo da Wikipédia sobre o Marco Civil da Internet. Na seção de "Ligações externas", é fornecido um link direto para a lei: **Lei nº 12 965, de 23 de abril de 2014 – Marco Civil da Internet no Brasil** (<http://www.planalto.gov.br/ccivil_03/_ato2011-2014/2014/lei/l12965.htm> - este link não estava nos trechos, mas é o link padrão do planalto para a lei citada no texto). Outro link citado é para o Decreto nº 8 771, de 11 de maio de 2016.

*   **"O MARCO CIVIL DA INTERNET E A RESPONSABILIDADE CIVIL DOS PROVEDORES EM RELAÇÃO ÀS PUBLICAÇÕES DE CONTEÚDOS DE TERCEIROS An - UNIFAN"**: O título completo deste documento é "O MARCO CIVIL DA INTERNET E A RESPONSABILIDADE CIVIL DOS PROVEDORES EM RELAÇÃO ÀS PUBLICAÇÕES DE CONTEÚDOS DE TERCEIROS An". Não há um link direto para o documento nos trechos, mas a seção de referências inclui links para decisões judiciais citadas:
    *   Jurisprudência TJDFT via Jusbrasil: <https://tj-df.jusbrasil.com.br/jurisprudencia/899288955/7226795120188070001-df-0722679-5120188070001>
    *   Jurisprudência TJMT via Jusbrasil: <https://tj-mt.jusbrasil.com.br/jurisprudencia/839613322/apelacao-civel-ac-170949320168110041-mt>
    *   Notícia STJ: <https://www.stj.jus.br/sites/portalp/Paginas/Comunicacao/Noticias/04122020-Responsabilizacao-de-provedor-de-aplicacao-por-conteudo-ofensivo-independe-de-notificacao-judicial.aspx#:~:text=%E2%80%8B%E2%80%8BA%20jurisprud%C3%AAncia%20do ,ficar%20demonstrado%20que%20houve%20ci%C3%AAncia>

*   **"Reflexões e orientações sobre a prática da psicoterapia - Conselho Federal de Psicologia"**: Este documento do Conselho Federal de Psicologia (CFP) tem como título "Reflexões e orientações sobre a prática da psicoterapia". Ele menciona que está disponível em <www.cfp.org.br>. A seção de referências inclui links para artigos da ABRAP:
    *   Artigo da ABRAP sobre normatização da psicoterapia: <http://www.abrap.org/normatizacao.php?NuNot=63>
    *   Artigo da ABRAP sobre reconhecimento e qualificação do psicoterapeuta: <abrap.org/normatizacao.php?NuNot=271>

*   **"TRIPARTIÇÃO DOS PODERES: A INFLUÊNCIA DO PODER EXECUTIVO SOBRE OS DEMAIS PODERES - UniRV"**: O título completo deste documento é "TRIPARTIÇÃO DOS PODERES: A INFLUÊNCIA DO PODER EXECUTIVO SOBRE OS DEMAIS PODERES". É associado à UniRV, mas não há um link direto para o documento nos trechos.

*   **"Tipos de Terapia: Saiba quais são e qual escolher - Psitto"**: Este artigo do blog Psitto tem o título "Tipos de Terapia: Saiba quais são e qual escolher". Os trechos fornecidos não contêm um link direto para o artigo.

*   **"discursos políticos, saberes e práticas Modelos de atenção à saúde de usuários de álcool e outras drogas - SciELO"**: Este artigo, hospedado na plataforma SciELO, tem o título "discursos políticos, saberes e práticas Modelos de atenção à saúde de usuários de álcool e outras drogas". Estão disponíveis links para download do PDF em português.

*   **"saúde mental e redução de danos na atenção primária: concepções e ações - SciELO"**: Este artigo, hospedado na plataforma SciELO, tem o título "saúde mental e redução de danos na atenção primária: concepções e ações". Estão disponíveis links para download do PDF em português e inglês.

*   **"um guia para familia do adicto.pdf"**: Embora o nome do arquivo sugira o título "um guia para familia do adicto", o documento é uma adaptação de um guia do Grupo Familiar Nar-Anon. É fornecido o site do Nar-Anon do Brasil: <http://www.naranon.org.br>. Este não é um link direto para o PDF do guia.

*   **"Álcool e Outras Drogas"**: O título completo deste guia da Secretaria Municipal de Saúde do Rio de Janeiro é "Álcool e outras drogas: tratamento e acompanhamento de pessoas com problemas relacionados ao uso de álcool e outras drogas". Contém links para outros guias e informações na Plataforma SUBPAV e o site da prefeitura do Rio:
    *   Guia de Referência Rápida em HIV/AIDS: <http://subpav.org/download/prot/GuiadeReferenciaRepidaemHIV_AIDS_versaoGUIA_miolo.pdf>
    *   Guia de Referência Rápida em ISTs: <http://subpav.org/download/prot/destaque/APS_DST_final_completo.pdf>
    *   Informações sobre equipes de Consultório na Rua na Plataforma SUBPAV: <http://subpav.org/download/prot/Equipes%20de%20Consultorio%20na%20Rua.pdf>
    *   Site da Secretaria Municipal de Saúde do Rio de Janeiro: <prefeitura.rio/web/sms>
      
