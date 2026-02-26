# AtlasX-Blip — Arquitetura Modular #

Este projeto implementa um fluxo conversacional para a AtlasX Logística Integrada utilizando uma arquitetura modular, onde cada funcionalidade é isolada em módulos com responsabilidades bem definidas.

O objetivo é facilitar manutenção, evolução, testes e reuso de componentes.

# Visão Geral da Arquitetura #

A aplicação é organizada por módulos funcionais, cada um responsável por uma parte específica do fluxo do usuário.

O módulo Principal atua como orquestrador, conectando os demais módulos e controlando a navegação entre eles.

Princípios adotados:

Separação de responsabilidades

Facilidade de extensão (novos fluxos/módulos podem ser adicionados sem quebrar os existentes)


# Módulos e Responsabilidades #


* Principal

Responsabilidade:

Orquestrar a navegação entre módulos

Definir o fluxo principal da aplicação

Centralizar decisões de roteamento

Atuar como “hub” da aplicação

* Boas-vindas


Responsabilidade:

Mensagem inicial para o usuário

Apresentação do serviço


* CPF-CNPJ

Responsabilidade:

Fluxo de consulta de Pessoa Física (CPF)

Fluxo de consulta de Pessoa Jurídica (CNPJ)


* IA

Responsabilidade:

Integrações com APIs de IA

Geração dinâmica de questionários/perguntas

Coleta estruturada de dados (nome, telefone, endereço e email)

Transformação de respostas da IA em estruturas utilizáveis pela aplicação

Isolamento total da lógica de IA para facilitar troca de provedor no futuro


* Cascata

Responsabilidade:

Centralizar inatividade

Estruturar respostas padrão para cada tipo de menu

Encaminhar o usuário conforme respostas anteriores


* ATH

Responsabilidade:

Atendimento humano

Direcionamento para erros persistentes


* Finalizacao

Responsabilidade:

Encerrar o fluxo

Exibir mensagens finais

Confirmar conclusão do processo

---

Link do Figma: https://www.figma.com/board/bkZiQI8e9BqwDqYwDTl6mn/Bem-vindo-ao-FigJam?node-id=0-1&t=verLf6XPyzy1q9Gy-1

Link do Bot: https://giani-pertuzatti-mll1b.chat.blip.ai/?appKey=aG1sYXRsYXN4cm91dGVyOmZlMDRiMGNlLTYxNDgtNGNiYy1hMzFhLTU4YTg1ODhiZWFlOA==&_gl=1*e0spvl*_ga*NTA3NTE5NTM2LjE3NTMxNTA0NDc.*_ga_8GVWK8YMGL*czE3NzIxNDA5MjIkbzkkZzEkdDE3NzIxNDU1OTgkajU5JGwwJGgxMzI5OTU1NDg1*_gcl_au*MTM2NzQ4ODkzNi4xNzcyMDQ4MTg3

---

Para importar os fluxos, será necessário criar um bot para cada pasta. O nome do bot no router deverá ser o nome da pasta.

<img width="395" height="667" alt="image" src="https://github.com/user-attachments/assets/a02d22cf-27e6-4005-80c5-90ce1054e032" />

No Router, um resource é adicionado
inputProcessing, do tipo texto, com o valor de inputProcessing.js que está na raiz.

No bot "Principal" as seguintes variáveis foram setadas (conforme json da collection).

<img width="414" height="610" alt="image" src="https://github.com/user-attachments/assets/394714cd-5617-4ac9-9d80-9d4b501df3e5" />

No bot "ATH" as seguintes variáveis foram setadas.

<img width="386" height="500" alt="image" src="https://github.com/user-attachments/assets/22a4e1d1-b26d-4831-a5e6-844f5cd38fc5" />

No bot "IA" as seguintes variáveis foram setadas.
urlOpenAI: https://api.openai.com/v1/chat/completions
openAIToken: {{OPENAI_KEY}}

<img width="388" height="559" alt="image" src="https://github.com/user-attachments/assets/15536209-8f28-49b2-9170-f594b8b34ac5" />
