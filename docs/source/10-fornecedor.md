<div class="top-accessibility-bar" style="display: flex; justify-content: flex-end; align-items: center; gap: 8px; margin: 10px 0;">
  <span style="font-size: 14px; color: #555; font-weight: bold;">Tamanho do texto:</span>
  <button onclick="diminuirFonte()" title="Diminuir texto" style="padding: 6px 12px; font-weight: bold; cursor: pointer; border: 1px solid #ccc; border-radius: 4px; background: #f8f9fa;">A-</button>
  <button onclick="resetarFonte()" title="Tamanho normal" style="padding: 6px 12px; font-weight: bold; cursor: pointer; border: 1px solid #ccc; border-radius: 4px; background: #f8f9fa;">A</button>
  <button onclick="aumentarFonte()" title="Aumentar texto" style="padding: 6px 12px; font-weight: bold; cursor: pointer; border: 1px solid #ccc; border-radius: 4px; background: #f8f9fa;">A+</button>
  
  <button onclick="window.print()" style="background-color: #0056b3; color: white; padding: 6px 16px; border: none; border-radius: 5px; font-size: 14px; cursor: pointer; box-shadow: 0 2px 4px rgba(0,0,0,0.2); margin-left: 10px;">
    🖨️ Imprimir ou baixar esta página
  </button>
</div>

<p style="font-weight: bold; color: #d9534f; margin-top: -5px; margin-bottom: 20px;">PÚBLICO-ALVO: DESENVOLVEDORES E INTEGRADORES DE SISTEMAS</p>

# 10. Módulo Fornecedor

O Módulo Fornecedor permite a consulta de dados cadastrais e situação dos fornecedores habilitados para participar de processos de contratação pública.

## 10.1. consultarFornecedor

Serviço que permite consultar dados cadastrais de fornecedores, incluindo informações sobre porte empresarial, natureza jurídica e situação de habilitação para licitar.

**Endpoint:** `https://dadosabertos.compras.gov.br/modulo-fornecedor/1_consultarFornecedor`  

**Método HTTP:** <span class="badge-get">GET</span>

**Exemplo de Requisição (cURL):**
```bash
curl -X 'GET' \
  'https://dadosabertos.compras.gov.br/modulo-fornecedor/1_consultarFornecedor' \
  -H 'accept: */*'
```

**Parâmetros da Solicitação:**

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| pagina | integer | <span class="badge-opt">⚪ Não</span> | Referente à paginação dos resultados. Permite ao usuário navegar entre as páginas de resultados. (Default: 1) |
| tamanhoPagina | integer | <span class="badge-opt">⚪ Não</span> | Ajustar o tamanho de registros por página (limite máx. de 500 registros por página). (Default: 10) |
| cnpj | string | <span class="badge-opt">⚪ Não</span> | CNPJ do fornecedor (sem máscara) |
| cpf | string | <span class="badge-opt">⚪ Não</span> | CPF do fornecedor (sem máscara) |
| naturezaJuridicaCodigoRFB | integer | <span class="badge-opt">⚪ Não</span> | Informação referente a natureza juridica codigo rfb |
| porteEmpresaId | integer | <span class="badge-opt">⚪ Não</span> | Código do porte da empresa |
| codigoCnae | integer | <span class="badge-opt">⚪ Não</span> | Código CNAE (Classificação Nacional de Atividades Econômicas) |
| ativo | boolean | <span class="badge-req">🔴 Sim</span> | Indica se o fornecedor está ativo. 0 – False/Inativo; 1 – True/Ativo |
| uf | string | <span class="badge-opt">⚪ Não</span> | Informação referente a uf |
| municipio | string | <span class="badge-opt">⚪ Não</span> | Informação referente a municipio |

**Dados de Retorno:**

| Campo | Tipo | Descrição |
|---|---|---|
| ativo | Booleano | Indica se o fornecedor está ativo |
| cnpj | Texto | CNPJ do fornecedor |
| cpf | Texto | CPF do fornecedor |
| habilitadoLicitar | Booleano | Indica se o fornecedor está habilitado para licitar |
| codigoCnae | Inteiro | Código CNAE do fornecedor |
| nomeCnae | Texto | Descrição da atividade CNAE |
| nomeMunicipio | Texto | Nome do município do fornecedor |
| naturezaJuridicaId | Inteiro | Código da natureza jurídica |
| naturezaJuridicaNome | Texto | Descrição da natureza jurídica |
| porteEmpresaId | Inteiro | Código do porte da empresa |
| porteEmpresaNome | Texto | Descrição do porte da empresa |
| nomeRazaoSocialFornecedor | Texto | Nome ou razão social do fornecedor |
| ufSigla | Texto | Sigla da unidade federativa (UF) do fornecedor |
| totalRegistros | Inteiro | Total de registros encontrados |
| totalPaginas | Inteiro | Total de páginas disponíveis |
| paginasRestantes | Inteiro | Número de páginas restantes |
| resultado | Texto/Número | Lista de registros retornados na página atual da consulta |
| nomeFantasia | Texto/Número | Informação referente a nome fantasia |
| naturezaJuridicaCodigoRFB | Texto/Número | Informação referente a natureza juridica codigo rfb |
| statusHabilitacaoGeral | Texto/Número | Informação referente a status habilitacao geral |
| email | Texto/Número | Informação referente a email |
| telefone | Texto/Número | Informação referente a telefone |
| socios | Texto/Número | Informação referente a socios |
| linhasFornecimento | Texto/Número | Informação referente a linhas fornecimento |

**Exemplo de Retorno:**
```json
{
  "resultado": [
    {
      "ativo": true,
      "cnpj": "string",
      "cpf": "string",
      "habilitadoLicitar": true,
      "codigoCnae": 0,
      "nomeCnae": "string",
      "nomeMunicipio": "string",
      "naturezaJuridicaId": 0,
      "naturezaJuridicaNome": "string",
      "porteEmpresaId": 0,
      "porteEmpresaNome": "string",
      "nomeRazaoSocialFornecedor": "string",
      "ufSigla": "string"
    }
  ],
  "totalRegistros": 0,
  "totalPaginas": 0,
  "paginasRestantes": 0
}
```

<a href="#">⬆️ Voltar ao topo</a>

## 10.2. consultarComprovanteNivelCadastramento

Serviço para obter dados e consultar o endpoint consultarComprovanteNivelCadastramento.

**Endpoint:** `https://dadosabertos.compras.gov.br/modulo-fornecedor/2_consultarComprovanteNivelCadastramento`  

**Método HTTP:** <span class="badge-get">GET</span>

**Exemplo de Requisição (cURL):**
```bash
curl -X 'GET' \
  'https://dadosabertos.compras.gov.br/modulo-fornecedor/2_consultarComprovanteNivelCadastramento' \
  -H 'accept: */*'
```

**Parâmetros da Solicitação:**

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| pagina | integer | <span class="badge-opt">⚪ Não</span> | Referente à paginação dos resultados. Permite ao usuário navegar entre as páginas de resultados. (Default: 1) |
| tamanhoPagina | integer | <span class="badge-opt">⚪ Não</span> | Ajustar o tamanho de registros por página (limite máx. de 500 registros por página). (Default: 10) |
| niFornecedor | string | <span class="badge-req">🔴 Sim</span> | Número de identificação do fornecedor (CPF/CNPJ/Estrangeiro) |
| tipoCertidaoId | integer | <span class="badge-opt">⚪ Não</span> | Informação referente a tipo certidao id |
| uf | string | <span class="badge-opt">⚪ Não</span> | Informação referente a uf |

**Dados de Retorno:**

| Campo | Tipo | Descrição |
|---|---|---|
| resultado | Texto/Número | Lista de registros retornados na página atual da consulta |
| niFornecedor | Texto/Número | Número de identificação do fornecedor (CPF/CNPJ/Estrangeiro) |
| nomeRazaoSocialFornecedor | Texto | Nome empresarial (razão social) ou nome completo do fornecedor |
| tipoCertidaoId | Texto/Número | Informação referente a tipo certidao id |
| tipoCertidaoNome | Texto/Número | Informação referente a tipo certidao nome |
| abrangencia | Texto/Número | Informação referente a abrangencia |
| dataValidade | Texto/Número | YYYY-MM-DD |
| situacao | Texto/Número | Informação referente a situacao |
| orgaoEmissorId | Texto/Número | Informação referente a orgao emissor id |
| orgaoEmissorNome | Texto/Número | Informação referente a orgao emissor nome |
| ufSigla | Texto | Sigla da unidade federativa (UF) do fornecedor |
| totalRegistros | Texto/Número | Total de registros encontrados |
| totalPaginas | Texto/Número | Total de páginas disponíveis |
| paginasRestantes | Texto/Número | Número de páginas restantes |

**Exemplo de Retorno:**
```json
{
  "resultado": [
    {
      "niFornecedor": "string",
      "nomeRazaoSocialFornecedor": "string",
      "tipoCertidaoId": 0,
      "tipoCertidaoNome": "string",
      "abrangencia": "string",
      "dataValidade": "2024-01-15 10:30:00",
      "situacao": "string",
      "orgaoEmissorId": 0,
      "orgaoEmissorNome": "string",
      "ufSigla": "string"
    }
  ],
  "totalRegistros": 0,
  "totalPaginas": 0,
  "paginasRestantes": 0
}
```

<a href="#">⬆️ Voltar ao topo</a>

## 10.3. consultarEstatisticoGeografico

Serviço para obter dados e consultar o endpoint consultarEstatisticoGeografico.

**Endpoint:** `https://dadosabertos.compras.gov.br/modulo-fornecedor/3_consultarEstatisticoGeografico`  

**Método HTTP:** <span class="badge-get">GET</span>

**Exemplo de Requisição (cURL):**
```bash
curl -X 'GET' \
  'https://dadosabertos.compras.gov.br/modulo-fornecedor/3_consultarEstatisticoGeografico' \
  -H 'accept: */*'
```

**Parâmetros da Solicitação:**

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| pagina | integer | <span class="badge-opt">⚪ Não</span> | Referente à paginação dos resultados. Permite ao usuário navegar entre as páginas de resultados. (Default: 1) |
| tamanhoPagina | integer | <span class="badge-opt">⚪ Não</span> | Ajustar o tamanho de registros por página (limite máx. de 500 registros por página). (Default: 10) |
| ufSigla | string | <span class="badge-req">🔴 Sim</span> | Informação referente a uf sigla |
| nomeMunicipio | string | <span class="badge-opt">⚪ Não</span> | Informação referente a nome municipio |
| codigoCnae | integer | <span class="badge-opt">⚪ Não</span> | Código CNAE (Classificação Nacional de Atividades Econômicas) |
| porteEmpresaId | string | <span class="badge-opt">⚪ Não</span> | Código do porte da empresa |

**Dados de Retorno:**

| Campo | Tipo | Descrição |
|---|---|---|
| resultado | Texto/Número | Lista de registros retornados na página atual da consulta |
| codigoCnae | Inteiro | Código CNAE do fornecedor |
| ufSigla | Texto | Sigla da unidade federativa (UF) do fornecedor |
| nomeMunicipio | Texto | Nome do município do fornecedor |
| tipoFornecedor | Texto/Número | Informação referente a tipo fornecedor |
| nomeCnae | Texto | Descrição da atividade CNAE |
| porteEmpresaId | Inteiro | Código do porte da empresa |
| porteEmpresaNome | Texto | Descrição do porte da empresa |
| totalEmpresasAtivas | Texto/Número | Informação referente a total empresas ativas |
| totalEmpresasPorPorte | Texto/Número | Informação referente a total empresas por porte |
| totalRegistros | Texto/Número | Total de registros encontrados |
| totalPaginas | Texto/Número | Total de páginas disponíveis |
| paginasRestantes | Texto/Número | Número de páginas restantes |

**Exemplo de Retorno:**
```json
{
  "resultado": [
    {
      "codigoCnae": 0,
      "ufSigla": "string",
      "nomeMunicipio": "string",
      "tipoFornecedor": "string",
      "nomeCnae": "string",
      "porteEmpresaId": 0,
      "porteEmpresaNome": "string",
      "totalEmpresasAtivas": 0,
      "totalEmpresasPorPorte": 0
    }
  ],
  "totalRegistros": 0,
  "totalPaginas": 0,
  "paginasRestantes": 0
}
```

<a href="#">⬆️ Voltar ao topo</a>

### 10.3.1. consultarEstatisticoGeograficoInternacional

Serviço para obter dados e consultar o endpoint consultarEstatisticoGeograficoInternacional.

**Endpoint:** `https://dadosabertos.compras.gov.br/modulo-fornecedor/3.1_consultarEstatisticoGeograficoInternacional`  

**Método HTTP:** <span class="badge-get">GET</span>

**Exemplo de Requisição (cURL):**
```bash
curl -X 'GET' \
  'https://dadosabertos.compras.gov.br/modulo-fornecedor/3.1_consultarEstatisticoGeograficoInternacional' \
  -H 'accept: */*'
```

**Parâmetros da Solicitação:**

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| pagina | integer | <span class="badge-opt">⚪ Não</span> | Referente à paginação dos resultados. Permite ao usuário navegar entre as páginas de resultados. (Default: 1) |
| tamanhoPagina | integer | <span class="badge-opt">⚪ Não</span> | Ajustar o tamanho de registros por página (limite máx. de 500 registros por página). (Default: 10) |
| paisCodigoIso | string | <span class="badge-opt">⚪ Não</span> | Informação referente a pais codigo iso |

**Dados de Retorno:**

| Campo | Tipo | Descrição |
|---|---|---|
| resultado | Texto/Número | Lista de registros retornados na página atual da consulta |
| paisCodigoIso | Texto/Número | Informação referente a pais codigo iso |
| paisNome | Texto/Número | Informação referente a pais nome |
| totalFornecedoresAtivos | Texto/Número | Informação referente a total fornecedores ativos |
| totalFornecedores | Texto/Número | Informação referente a total fornecedores |
| totalRegistros | Texto/Número | Total de registros encontrados |
| totalPaginas | Texto/Número | Total de páginas disponíveis |
| paginasRestantes | Texto/Número | Número de páginas restantes |

**Exemplo de Retorno:**
```json
{
  "resultado": [
    {
      "paisCodigoIso": "string",
      "paisNome": "string",
      "totalFornecedoresAtivos": 0,
      "totalFornecedores": 0
    }
  ],
  "totalRegistros": 0,
  "totalPaginas": 0,
  "paginasRestantes": 0
}
```

<a href="#">⬆️ Voltar ao topo</a>

<div class="bottom-print-bar" style="text-align: right; margin: 20px 0;">
  <button onclick="window.print()" style="background-color: #0056b3; color: white; padding: 10px 20px; border: none; border-radius: 5px; font-size: 16px; cursor: pointer; box-shadow: 0 2px 4px rgba(0,0,0,0.2);">
    🖨️ Imprimir ou baixar esta página
  </button>
</div>
