---
title: Documentação SISPRO

language_tabs: # must be one of https://git.io/vQNgJ
  - ruby
  - shell
  - javascript
toc_footers:
  - <a href='https://github.com/lord/slate'>Documentação feita com Slate</a>

search: true
---

# Introdução

Bem-vindo(a) documentação do SISPRO API, você poderá ver como receber informações pertinentes aos processos relacionados a UFF e a FEC.

# Autenticação

```ruby
require 'sispro'

api = Sispro::APIClient.authorize!('sua-chave')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: sua-chave"
```

```javascript
const sispro = require('sispro');

let api = sispro.authorize('sua-chave');
```

SISPRO utiliza chaves API para permitir acesso à API. Você pode registrar uma nova chave API do SISPRO no [portal](https://app.homologacao.uff.br/sispro)

A API recebe a solicitação desta forma:

`Authorization: sua-chave`

<aside class="notice">
Você deve substituir <code>sua-chave</code> pela sua chave API pessoal.
</aside>

# Solicitação de Proposta Comercial

## Descricao de Campos

```json
  {
    informacoes_basicas:{
      orgao_proponente: "orgao proponente",
      departamento: "departamento",
      titulo: "titulo do projeto",
      tipo: "tipo do projeto"
      orgao_financiador: "fec",
      tipo_financiamento: "contrato",
      local: {
        endereco: "Rua Miguel de Frias, 123",
        complemento: "",
        bairro: "Icaraí",
        cep: "24.220-001",
        estado: "Rio de Janeiro",
        cidade: "Niterói"
      },
      coordenador:{
        nome: "Fulano 01",
        lotacao: "Superintendência de Tecnologia da Informação - STI",
        cpf: "123.456.789-00",
        rg:"12.345.678-9",
        orgao_expedidor: "DETRAN-RJ",
        telefone_fax: "24578654",
        email: "mail1@id.uff.br",
        cargo: "Analista de Tecnologia da Informação"
      },
      fiscal:{
        nome: "Fulano 02",
        lotacao: "Superintendência de Tecnologia da Informação - STI",
        cpf: "123.456.789-01",
        rg:"12.345.678-0",
        orgao_expedidor: "DETRAN-RJ",
        telefone_fax: "21578654",
        email: "mail2@id.uff.br",
        cargo: "Assistente em Administração",
        funcao: "",
        matricula_siape: "1234567"
      }
    },
    participe:{
      entidada: "FUNDAÇÃO EUCLIDES DA CUNHA DE APOIO INSTITUCIONAL A UFF",
      cnpj: "03.438.229/0001-09",
      telefone: "(00)0000-0000",
      endereco: "Rua Miguel de Frias, 123",
      complemento: "",
      bairro: "Icaraí",
      cep: "24.220-001",
      estado: "Rio de Janeiro",
      cidade: "Niterói"
    },
    detalhes:{
      periodo_inicio: "10/10/2019",
      periodo_fim: "31/01/2020",
      contextualizacao: "Contextualização",
      identificacao: "Identificação",
      justificativa_proposicao: "Justificativa",
      metodologia_selecao_bolsistas:"Descrição da metodologia e critérios para seleção de bolsistas"
    }
  } 
  ```

### Órgão Proponente
  Descrição: Preencher o nome/SIGLA da unidade de ensino ou unidade administrativa (Pró-Reitoria/ Superintendência) ao qual o projeto está vinculado.
### Departamento
  Descrição: Preencher o nome/SIGLA do departamento de ensino ou setor/coordenação ao qual o projeto está vinculado.
### Título do Projeto
  Descrição: Preencher o Título do Projeto.
### Tipo do Projeto (Pesquisa, Extensão, Desenvolvimento Institucional e Ensino)
  Descrição: 'Preencher o tipo de projeto, de acordo com as definições que podem ser encontradas na Resolução nº 26/2017. Obs.: Projetos de Ensino não contemplados pela Resolução 155/2008'
### Nome do Curso
  Descrição: Preencher com o nome do curso.
### Tipo do Curso (Atualização, Extensão, Aperfeiçoamento, Pós-Graduação Stricto sensu, Pós-Graduação Lato Sensu)
  Descrição: Preencher com o tipo do curso.
### Tipo de Turma
  Descrição: "Turma Contrato: Turma fechada, financiada por empresa privada/pública\n
              Turma Auto sustentável: Turma aberta ao público."
### Tipo de Arrecação (UFF/FEC)
  Descrição: Arrecadação UFF: significa que os recursos financeiros do projeto já estão ou ingressarão na UFF, que os transferirá à FEC mediante pagamento de nota fiscal por esta emitida. 
  Arrecadação FEC: significa que os recursos financeiros serão arrecadados diretamente pela FEC.
### Endereço de execução do projeto
  Descrição: Endereço do departamento ou do setor administrativo ao qual o projeto está vinculado.
### Fiscal
  Descrição: Servidor (docente ou técnico administrativo) indicado para acompanhar e fiscalizar a execução das atividades do contrato, bem como atestar  notas fiscais e relatórios de prestacão de contas, conforme art.67 da Lei 8.666/93 e Resolução nº 26/2017. O mesmo não poderá ser participante do projeto.
### Assistente
  Descrição: Assistente designado, pelo coordenador, ao projeto em questão.
### Nome Entidade
  Descrição: Nome da fundação a ser contratada para apoio ao gerenciamento e à execução das atividades relativas ao projeto.
### Contextualização
  Descrição: Resumo das principais características do projeto ou curso, suas ações,  público-alvo,  objetivos gerais e específicos e o resultado esperado.
### Identificação do objeto
  Descrição: Breve descrição do projeto ou curso.
### Justificativa da proposição
  Descrição: Justificar a necessidade e interesse na proposição do projeto, a partir da demanda  existente na Universidade e dos benefícios que serão alcançados ao fim do projeto.
### Descrição da metodologia e critérios para seleção de bolsistas
  Descrição: Preencher com a forma pela qual todos os participantes (docentes, técnicos, discentes e autônomos) do projeto foram escolhidos. Ex.: análise de currículo, dinâmica, entrevista, etc.
### Subcoordenador
  Descrição: O subcoordenador é o substituto eventual do coordenador no projeto. Pode realizar todas as ações que o coordenador realiza.

  
## Proposta Comercial


```json
{
  detalhes:{
    valor: 100,
  },
  itens:{
    diaria_civil:{
      diaria_nacional: true,
      diaria_internacional: false,
      diaria_de_campo: false
    },
    bolsa_ensino:{
      docente: 5,
      tecnico_administrativo: 0,
      pesquisador_visitante: 0,
      discente: 0
    },
    material_consumo:{
      material_consumo_nacional: false,
      material_consumo_internacional: false
    },
    passagens_locomocao:{
      aerea_nacional: false,
      aerea_internaciona: false,
      terrestre_nacional: false,
      terrestre_inteernacional: false,
      aquaviaria_nacional: false,
      aquaviaria_internacional: false
    },
    terceiros_fisica:{
      celetista: 0,
      autonomo: 0
    },
    terceiros_juridica:{
      aluguel: false,
      terceiros_exterior: false,
      importacao: false,
      docencia: false,
      aluguel_carro: false,
      aluguel_barco: false,
      servicos_graficos: false
    },
    equipamentos_material_permanente:{
      equipamentos: false,
      material_permanente: false
    },
    observacoes: "observacoes",
    receitas_previstas:{
      tipo_receita: "contrato",
      valor: 20000.00,
      fonte: "1201584813",
      total_receitas: 20000.00
    }
  }
}

```
