# Aplicação de RAG para Responder Perguntas Médicas sobre Tratamento do Tabagismo

<p align="center">
   <img src="http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=RED&style=for-the-badge" #vitrinedev/>
</p>

### Tópicos 

- [Descrição](#descrição-do-projeto)

- [Objetivo](#objetivo)

- [Contexto](#contexto)

- [Como Usar](#como-usar)

- [Autor](#autor)


## Descrição
Este projeto consiste em uma aplicação em Python que utiliza a técnica de **Retrieval Augmented Generation (RAG)** para responder a perguntas específicas de médicos sobre o protocolo de tratamento do tabagismo. O modelo utilizado é o **LLM Bode baseado em llama 2**, com textos em português. O modelo pode ser encontrado em [Hugging Face Model Hub](https://huggingface.co/recogna-nlp/bode-7b-alpaca-pt-br-no-peft).

A aplicação é integrada com **FastAPI** e acessível através de uma URL pública do **Ngrok**.

## Objetivo
O objetivo principal deste projeto é fornecer aos médicos uma ferramenta que possa rapidamente e com precisão fornecer informações específicas contidas no "Protocolo Clínico e Diretrizes Terapêuticas do Tabagismo" disponibilizado pelo **INCA (Instituto Nacional de Câncer)**. Ao simplificar o acesso a essas informações, a aplicação visa apoiar os médicos na tomada de decisões e na prestação de cuidados baseados em evidências aos pacientes.

## Contexto
O acesso rápido e preciso a informações específicas dentro de protocolos clínicos é crucial para apoiar médicos na tomada de decisões e no fornecimento de cuidados baseados em evidências aos pacientes. Este projeto foca em simplificar o acesso às informações contidas no "Protocolo Clínico e Diretrizes Terapêuticas do Tabagismo" do INCA.

## Dados
O projeto utiliza o **protocolo de tratamento do tabagismo disponibilizado pelo INCA**, acessível no seguinte [link:INCA](https://www.inca.gov.br/sites/ufu.sti.inca.local/files//media/document//protocolo-clinico-e-diretrizes-terapeuticas-do-tabagismo.pdf). Este documento contém diretrizes clínicas detalhadas que servirão como base para o sistema responder às perguntas dos médicos.

## Como Usar
Exemplo de uso para a pergunta: "O que fazer em caso de recaída?"
![alt text](<Screenshot 2024-04-08 at 06.13.44.png>)

"""Use o contexto a seguir (delimitado por <ctx></ctx>) e o histórico do chat (delimitado por <hs></hs>) para responder à pergunta:
------
<ctx> a expectativa de vida, melhorar a saúde e a qualidade de vida. Aqueles idosos que decidem 
fazer uma tentativa têm elevada taxa de sucesso (35,36). 
 
6.5. Pacientes com tuberculose  
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
