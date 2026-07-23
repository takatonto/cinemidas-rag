# CineMidas RAG

Agente corporativo baseado em RAG para responder dúvidas frequentes sobre os serviços de uma rede fictícia de cinemas.

> Projeto desenvolvido para o Challenge Alura Agente.

## Status do projeto

Em desenvolvimento.

## Problema

Colaboradores de uma rede de cinemas precisam consultar diferentes regras para responder dúvidas sobre ingressos, cancelamentos, pagamentos, acessibilidade e outros serviços.

A busca manual por essas informações pode tornar o atendimento demorado e gerar respostas inconsistentes. É visado, também, a diminuição de custos com o atendimento ao cliente online.

## Solução proposta

O CineMidas será um agente de inteligência artificial capaz de responder perguntas utilizando como fonte o Manual de Atendimento da Rede CineViva, uma empresa fictícia criada para este projeto.

A aplicação utilizará uma arquitetura RAG para localizar informações relevantes no documento antes de gerar uma resposta.

## Público-alvo

O agente será destinado aos colaboradores da Rede CineViva, especialmente às equipes de:

- Atendimento ao cliente.
- Bilheteria.
- Bomboniere.
- Suporte digital.
- Operações das unidades.

## Objetivos

- Processar um manual de atendimento em PDF.
- Responder perguntas com base no conteúdo do documento.
- Apresentar respostas claras e objetivas.
- Informar a fonte utilizada na resposta.
- Reconhecer perguntas sem resposta no documento.
- Disponibilizar uma interface online.
- Implantar a aplicação na Oracle Cloud Infrastructure.

## Escopo inicial

O agente poderá responder dúvidas sobre:

- Compra de ingressos.
- Formas de pagamento.
- Meia-entrada.
- Cancelamentos e reembolsos.
- Troca de sessões e assentos.
- Classificação indicativa.
- Acessibilidade.
- Alimentos e bebidas.
- Programa de fidelidade.
- Sessões canceladas.
- Objetos perdidos.
- Canais de atendimento.

## Limitações

O CineMidas não poderá:

- Vender ou cancelar ingressos.
- Consultar pedidos reais.
- Processar pagamentos ou reembolsos.
- Acessar dados pessoais.
- Alterar cadastros.
- Criar regras que não estejam presentes no documento.
- Autorizar exceções às políticas da empresa.

## Arquitetura preliminar

```mermaid
flowchart LR
    A[Pergunta do colaborador] --> B[Interface do CineMidas]
    B --> C[Busca de trechos relevantes]
    D[Manual de atendimento em PDF] --> C
    C --> E[Contexto recuperado]
    E --> F[Modelo de linguagem]
    F --> G[Resposta com indicação da fonte]
```

## Perguntas planejadas

O CineMidas será desenvolvido para responder perguntas como:

- Até quando posso cancelar um ingresso comprado pelo aplicativo?
- A taxa de conveniência é devolvida em um cancelamento?
- O que acontece quando o cliente não comprova o direito à meia-entrada?
- Posso transferir meu ingresso para outra sessão?
- Todas as sessões possuem audiodescrição?
- É permitido entrar com alimentos comprados fora do cinema?
- Como funcionam os pontos do CineViva Club?
- Por quanto tempo um objeto perdido fica guardado?

O agente também será avaliado com perguntas que não possuem resposta no documento, solicitações de acesso a pedidos e pedidos de exceção às políticas.

## Tecnologias planejadas

A implementação inicial utilizará:

- **Python:** linguagem principal do projeto.
- **LangChain:** organização do fluxo de RAG.
- **PyPDF:** extração do conteúdo do manual em PDF.
- **Google Gemini:** geração das respostas e criação de representações semânticas.
- **Base vetorial local:** armazenamento e pesquisa dos trechos do documento.
- **Streamlit:** interface de perguntas e respostas.
- **Python dotenv:** leitura das variáveis de ambiente locais.
- **Oracle Cloud Infrastructure Compute:** hospedagem da aplicação.

As tecnologias poderão ser ajustadas caso os testes revelem problemas de compatibilidade ou implantação.

## Fluxo planejado da aplicação

1. A aplicação carrega o Manual de Atendimento da Rede CineViva em PDF.
2. O texto é extraído e dividido em trechos menores.
3. Cada trecho recebe uma representação semântica.
4. Os trechos são armazenados em uma base vetorial.
5. A pergunta do colaborador é utilizada para localizar os trechos mais relevantes.
6. Os trechos recuperados são enviados ao Gemini como contexto.
7. O Gemini gera uma resposta fundamentada no manual.
8. A interface apresenta a resposta e as fontes consultadas.

## Configuração de credenciais

A chave da API do Gemini deverá ser informada por meio da variável de ambiente:

GEMINI_API_KEY
