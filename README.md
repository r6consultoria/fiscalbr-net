[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/orochasamuel/fiscalbr-net/dotnet.yml)](https://github.com/orochasamuel/fiscalbr-net/actions/workflows/dotnet.yml)
# FiscalBr.NET [![Build Status](https://github.com/orochasamuel/fiscalbr-net/actions/workflows/dotnet.yml/badge.svg)](https://github.com/orochasamuel/fiscalbr-net/actions/workflows/dotnet.yml) [![GitHub issues](https://img.shields.io/github/issues/orochasamuel/fiscalbr.net)](https://github.com/orochasamuel/FiscalBr.NET/issues) [![GitHub](https://img.shields.io/github/license/orochasamuel/fiscalbr.net)](https://github.com/orochasamuel/FiscalBr.NET/blob/master/LICENSE)
[![Nuget](https://img.shields.io/nuget/v/FiscalBr.Common?color=red&label=Common)](https://www.nuget.org/packages/FiscalBr.Common/) [![Nuget](https://img.shields.io/nuget/v/FiscalBr.Dimob?label=Dimob)](https://www.nuget.org/packages/FiscalBr.Dimob/) [![Nuget](https://img.shields.io/nuget/v/FiscalBr.ECF?label=ECF)](https://www.nuget.org/packages/FiscalBr.ECF/) [![Nuget](https://img.shields.io/nuget/v/FiscalBr.EFDContribuicoes?label=EFD%20Contribuições)](https://www.nuget.org/packages/FiscalBr.EFDContribuicoes/) [![Nuget](https://img.shields.io/nuget/v/FiscalBr.EFDFiscal?label=EFD%20Fiscal)](https://www.nuget.org/packages/FiscalBr.EFDFiscal/)  [![Nuget](https://img.shields.io/nuget/v/FiscalBr.Sintegra?label=Sintegra)](https://www.nuget.org/packages/FiscalBr.Sintegra/)

###### SITE OFICIAL DO SPED: http://sped.rfb.gov.br/
Biblioteca gratuita  - desenvolvida com Visual Studio Community 2022 - para geração dos arquivos SPED e demais declarações necessárias no cenário contábil/fiscal brasileiro.

## TODO

- [ ] Implementar Factory Pattern.
- [ ] Mapear enums restantes do SPED.
- [x] Implementar leitura dos layouts. (Implementado completamente SPED Fiscal e Contribuições)
- [ ] Melhorar performance na geração das linhas.

## Apoiadores [![Donate](https://img.shields.io/badge/apoia.se-FiscalBr-green)](https://apoia.se/fiscalbr) [![Coffee](https://img.shields.io/badge/buy%20me%20a-coffee-yellow)](https://www.buymeacoffee.com/orochasamuel)

Se as bibliotecas lhe ajudaram ou contribuiram de alguma forma, apoie. :D Ajude a dar continuidade nesse projeto.

###### Últimos Apoios

[@rodrigofornasier](https://github.com/rodrigofornasier)

## Declarações

###### Projeto SPED

- [x] EFD Fiscal (ICMS/IPI)
- [x] EFD Contribuições (PIS/COFINS)
- [x] Escrituração Contábil Fiscal (ECF)
- [ ] Escrituração Contábil Digital (ECD)

###### Outras

- [x] DIMOB
- [x] SINTEGRA

## Exemplos

###### EFD ICMS IPI

- Exemplo de leitura, manuseio, recalculo do bloco 9 e escrita do arquivo:
```
var sped = new ArquivoEFDFiscal();
sped.Ler(camiho_do_arquivo_original, encoding_do_arquivo);

//Manuesar, ex: adicionar Bloco H

sped.GerarLinhas();
sped.CalcularBloco9();
sped.Escrever(camiho_do_arquivo_modificado);
```

###### EFD Contribuições

- Exemplo de Preenchimento do Bloco F - Registro 200

```cs
var listaLinhasArquivo = new List<string>();

var competencia = new DateTime(dataInicial.Year, dataInicial.Month, 1);

var listaContratos = ObtemListaContratosNoPeriodo(dataInicial, dataFinal);

var totalLinhasF200 = 0;

/* Cada contrato imobiliário gera um registro F200 */
foreach (var objContrato in listaContratos) {
  var registroF200 = new BlocoF.EfdContribRegF200 {
    // Preenche informações
  };

  /* adiciona nas linhas do arquivo */
  listaLinhasArquivo.Add(registroF200.EscreverCampos(competencia));
  totalLinhasF200++;
}
```

## Dúvidas?

Abra um issue na página do projeto no GitHub ou [clique aqui](https://github.com/orochasamuel/FiscalBr.NET/issues).

## Licença

[MIT](https://github.com/orochasamuel/FiscalBr.NET/blob/master/LICENSE)
