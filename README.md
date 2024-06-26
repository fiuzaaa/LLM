
# Aplicação de RAG para Responder Perguntas Médicas sobre Tratamento do Tabagismo

<p align="center">
   <img src="http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=RED&style=for-the-badge" #vitrinedev/>
</p>

### Tópicos 

- [Descrição](#descrição-do-projeto)

- [Objetivo](#objetivo)

- [Contexto](#contexto)

- [Dados](#dados)

- [RAG](#rag)

- [Como Usar](#como-usar)

- [Autor](#autor)


## Descrição
Este projeto consiste em uma aplicação em Python que utiliza a técnica de **Retrieval Augmented Generation (RAG)** para responder a perguntas específicas de médicos sobre o protocolo de tratamento do tabagismo. O modelo utilizado é o **LLM Bode baseado em llama 2**, com textos em português. O modelo pode ser encontrado em [Hugging Face Model Hub](https://huggingface.co/recogna-nlp/bode-7b-alpaca-pt-br-no-peft).

A aplicação é integrada com **FastAPI** e acessível através de uma URL pública do **Ngrok**.

## Objetivo
O objetivo principal deste projeto é fornecer aos médicos uma ferramenta que possa rapidamente e com precisão fornecer informações específicas contidas no "Protocolo Clínico e Diretrizes Terapêuticas do Tabagismo" disponibilizado pelo **INCA (Instituto Nacional de Câncer)**. Ao simplificar o acesso a essas informações, a aplicação visa apoiar os médicos na tomada de decisões e na prestação de cuidados baseados em evidências aos pacientes.

## Contexto
O acesso rápido e preciso a informações específicas dentro de protocolos clínicos é crucial para apoiar médicos na tomada de decisões e no fornecimento de cuidados baseados em evidências aos pacientes. Este projeto foca em simplificar o acesso às informações contidas no "Protocolo Clínico e Diretrizes Terapêuticas do Tabagismo" do INCA.
A utilização do banco de dados vetorial ChromaDB desempenhou um papel fundamental na contextualização do modelo de prompt. O ChromaDB serviu como uma fonte de embeddings essenciais, facilitando a inferência do RAG (Retrieval Augmented Generation). Para esta etapa crucial, empregou-se o modelo disponibilizado em [Hugging Face Model Hub](https://huggingface.co/tgsc/sentence-transformer-ult5-pt-small), o qual foi integrado ao ChromaDB para gerar embeddings relevantes e representativos.

Ao incorporar o ChromaDB com os embeddings gerados pelo modelo fornecido, conseguimos estabelecer uma base sólida para a inferência do RAG. Esses embeddings capturam nuances semânticas e relações contextuais, permitindo que o sistema responda de forma mais precisa e significativa às consultas médicas sobre o protocolo de tratamento do tabagismo.

Essa abordagem detalhada de integração do ChromaDB com os embeddings do modelo não apenas enriquece a compreensão do contexto, mas também melhora significativamente a capacidade do sistema de responder de maneira eficaz e relevante às perguntas médicas específicas sobre o tratamento do tabagismo.



## Dados
O projeto utiliza o **protocolo de tratamento do tabagismo disponibilizado pelo INCA**, acessível no seguinte [link:INCA](https://www.inca.gov.br/sites/ufu.sti.inca.local/files//media/document//protocolo-clinico-e-diretrizes-terapeuticas-do-tabagismo.pdf). Este documento contém diretrizes clínicas detalhadas que servirão como base para o sistema responder às perguntas dos médicos.

Um aspecto crucial na criação dos embeddings da base vetorial foi o processo de particionamento do documento em chunks de 500 palavras, com um overlap de 100 palavras. Esse método permitiu uma representação mais abrangente e detalhada do conteúdo do documento dentro do ChromaDB. Cada chunk foi processado individualmente, garantindo que nenhum detalhe fosse perdido durante a geração dos embeddings.

Essa estratégia de particionamento e sobreposição desempenhou um papel vital na captura da riqueza semântica e contextual do documento original. Ao dividir o texto em chunks menores e sobrepor parte do conteúdo entre eles, conseguimos garantir uma continuidade e coesão na representação dos embeddings.

Além disso, o tamanho dos chunks foi cuidadosamente escolhido para equilibrar a granularidade dos dados e a eficiência computacional. Chunks menores poderiam capturar detalhes mais finos, enquanto um overlap adequado garantia a coesão entre os embeddings gerados.

Essa abordagem detalhada no processo de criação dos embeddings da base vetorial não apenas enriqueceu a representação do documento no ChromaDB, mas também contribuiu significativamente para a capacidade do sistema de inferir respostas relevantes e precisas às consultas médicas sobre o protocolo de tratamento do tabagismo. A inclusão dessa informação no processo de contextualização do modelo de prompt fortaleceu ainda mais a robustez e a eficácia do sistema no fornecimento de informações úteis e confiáveis aos profissionais de saúde.


## RAG
![alt text](RAG_bode.png)


## Como Usar
Exemplo de uso para a pergunta: "O que fazer em caso de recaída?"
![alt text](<Screenshot 2024-04-08 at 06.13.44.png>)

"""Use o contexto a seguir (delimitado por <ctx></ctx>) e o histórico do chat (delimitado por <hs></hs>) para responder à pergunta:
------
<ctx> O tratamento do tabagismo pode ser iniciado em qualquer nível de ate nção à 
saúde, sendo preferencialmente na Atenção Primária à Saúde (APS). Ao término do 
tratamento , caso seja alcançada a abstinência, recomenda -se que o paciente seja 
acompanhado por até um ano para o apoio na manutenção deste quadro.  
No caso de recaída, deve -se reavaliar o tratamento feito anteriormente e 
decidir  em conjunto  como  proceder  em relação  ao retratamento.  Sugere -se ainda  a busca

os tabagistas com contraindicação ao uso do respectivo medicamento.  
 
6. CASOS ESPECIAIS  
 
6.1. Casos de recaída  
É indicado que tabagistas previamente tratados e que tenham apresentado 
recaída recebam incentivo para realizar novamente  o tratamento do tabagismo, sempre 
valorizando as experiências  por eles vividas nas tentativas anteriores de cessação. Acolher 
o paciente na sua totalidade, reforçar os ganhos, destacando a sua importante decisão de

decidir  em conjunto  como  proceder  em relação  ao retratamento.  Sugere -se ainda  a busca  
ativa  de pacientes que tenham abandonado o  tratamento.  
Os possíveis efeitos adversos pelo uso dos  medicamentos, já relatados, 
devem ser acompanhados pelo profissional da saúde responsável pelo atendimento, que irá 
decidir sobre  a melhor conduta a ser adotada em cada caso, fazendo , quando necessário, 
...
O que fazer em caso de recaida?
Resposta:

Em caso de recaída, é importante que o paciente seja acompanhado por até um ano para o apoio na manutenção do tratamento. Também é importante que o profissional da saúde responsável pelo atendimento avalie o tratamento feito anteriormente e decida em conjunto como proceder em relação ao retratamento. Além disso, é importante que o paciente seja incentivado a realizar novamente o tratamento do tabagismo, sempre valorizando as experiências por eles vividas nas tentativas anteriores de cessação."""

Exemplo de uso para a segunda pergunta: "Pacientes com tuberculose"
![alt text](<Screenshot 2024-04-08 at 06.12.51.png>)

Use o contexto a seguir (delimitado por <ctx></ctx>) e o histórico do chat (delimitado por <hs></hs>) para responder à pergunta:
------
<ctx> a expectativa de vida, melhorar a saúde e a qualidade de vida. Aqueles idosos que decidem 
fazer uma tentativa têm elevada taxa de sucesso (35,36). 
 
"""6.5. Pacientes com tuberculose  
Segundo dados da OMS, mais de 20% da incidência global de tuberculose 
pode ser atribuída ao tabagismo, que aumenta em duas vezes e meia o risco d essa doença. 
Tabagistas sem história anterior de tuberculose apresentam risco de morte por essa  doença

ser uma parte integrante do cuidado do paciente com tuberculose ( 38-40). 
É indicado  que portadores  de tuberculose,  em qualquer  fase do tratamento,  
sejam  tratados  da dependência à nicotina e utilizem as mesmas medidas  terapêuticas 
empregadas para a população em geral. O tratamento preconizado é a associação de 
aconselhamento estruturado com farmacoterapia ( 36). 
 
 
6.6. Pacientes com câncer  
A identificação do tabagismo  e as intervenções para a sua cessação são

Tabagistas sem história anterior de tuberculose apresentam risco de morte por essa  doença 
nove vez es maior quando comparados com os que nunca fumaram. Ao parar de fumar, o 
risco de morte por tuberculose reduz -se cerca de 65% em comparação aos que continuam a 
fumar ( 37). 
...
 Pacientes com tuberculose
Resposta:

Os pacientes com tuberculose devem ser tratados da dependência à nicotina e utilizar as mesmas medidas terapêuticas empregadas para a população em geral. Além disso, é importante que os pacientes com tuberculose sejam acompanhados por um profissional da saúde responsável pelo atendimento, que irá decidir sobre a melhor conduta a ser adotada em cada caso, fazendo, quando necessário, encaminhamentos para outros profissionais ou unidades de saúde."""


A resposta da segunda pergunta traz à memória da primeira pergunta para resposta.

## Autor
[<br><sub>Raphael Fiuza</sub>](https://github.com/fiuzaaa)
