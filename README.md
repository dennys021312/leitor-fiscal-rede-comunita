[README.md](https://github.com/user-attachments/files/34974626/README.md)
# Leitor e Validador Fiscal — Rede Comunitá

Aplicação web de apoio à leitura de notas fiscais, consultas públicas e apuração indicativa de retenções. Esta edição trabalha com **uma nota por vez**: ao carregar uma nova nota, a análise anterior é reiniciada. Não há cadastro de usuários, histórico de documentos, banco de dados ou log de atividades.

## Como abrir

1. Extraia o ZIP.
2. Abra `index.html` no Chrome ou Edge.
3. Mantenha a internet ativa para carregar as bibliotecas de leitura de PDF/OCR e realizar consultas públicas.
4. Clique em **Selecionar nota** e escolha um arquivo.
5. Confira os campos identificados, ajuste os dados necessários e escolha os enquadramentos tributários antes de calcular.

Para evitar bloqueios de navegador, o ideal é publicar o `index.html` no GitHub Pages (HTTPS) ou usar um servidor local.

## Formatos aceitos

- XML de NF-e e NFS-e: leitura estruturada quando o leiaute é reconhecido.
- PDF com texto: extração local pelo PDF.js.
- PDF escaneado e imagens PNG/JPG/JPEG/WEBP: OCR em português pelo Tesseract.js, carregado sob demanda.
- TXT, JSON e HTML: leitura assistida por padrões.

## Funcionalidades

- Leitura automática do número, data, emitente/prestador, CNPJ, tomador, descrição, códigos, município e valor quando presentes e reconhecidos.
- Quadro de conferência que informa campos encontrados e itens não identificados.
- Consulta pública de CNPJ por bases de terceiros, com acesso ao comprovante oficial da Receita Federal.
- Atalho para consulta pública de NFS-e pela chave de acesso no portal nacional.
- Memória de cálculo indicativa de CSRF, INSS, ISS e IRRF, mediante enquadramento informado pelo responsável.
- Parecer de conferência copiável e imprimível.
- Base legal e explicação dos limites de cada consulta.

## Privacidade e ausência de histórico

Os arquivos são processados no navegador. Esta página não grava documentos em banco de dados, não usa `localStorage` ou `sessionStorage` e não mantém histórico. Ao selecionar uma nova nota ou clicar em **Nova análise**, os campos, resultados e dados temporários da análise anterior são limpos. Consultas externas feitas nos provedores são regidas pelas políticas desses próprios serviços.

## Limites importantes

- APIs públicas de CNPJ são bases de terceiros, não consulta em tempo real diretamente à Receita Federal; podem ter defasagem. Confirme no comprovante oficial.
- A consulta oficial de NFS-e abre o portal público. Esta página não acessa documentos protegidos nem contorna certificado digital.
- O OCR depende de conexão para carregar o mecanismo e o pacote de idioma português. O reconhecimento pode confundir caracteres e valores; confira o documento original.
- A leitura é assistiva. XML estruturado tende a ser mais confiável que OCR/PDF. Campos não identificados precisam de conferência manual.
- A apuração de retenções é indicativa. A incidência depende do serviço efetivamente prestado, contrato, regime tributário, município e legislação vigente. O cálculo não constitui parecer contábil definitivo nem autorização de pagamento.
- A integração oficial de apuração da CBS exige credenciais, autenticação e backend seguro; não está incluída nesta página estática.

## Publicar no GitHub Pages

1. Crie um repositório no GitHub.
2. Envie `index.html` para a raiz do repositório.
3. Em **Settings → Pages**, selecione a branch principal e a pasta `/ (root)`.
4. Abra o endereço HTTPS publicado.

## Referências

- Receita Federal — CNPJ alfanumérico: https://www.gov.br/receitafederal/pt-br/acesso-a-informacao/acoes-e-programas/programas-e-atividades/cnpj-alfanumerico
- Receita Federal — comprovante CNPJ: https://solucoes.receita.fazenda.gov.br/Servicos/cnpjreva/
- CNPJ.ws — API pública: https://docs.cnpj.ws/referencia-de-api/api-publica/consultando-cnpj
- Lei 10.833/2003: https://www2.camara.leg.br/legin/fed/lei/2003/lei-10833-29-dezembro-2003-497045-normaatualizada-pl.html
- IN RFB 2.110/2022: https://normas.receita.fazenda.gov.br/sijut2consulta/normas.receisulta/link.action?idAto=126687&visao=compilado
- Lei Complementar 116/2003: https://www.planalto.gov.br/ccivil_03/leis/lcp/lcp116.htm
- Portal Nacional da NFS-e: https://www.nfse.gov.br/consultapublica
- Documentação da API de apuração da CBS: https://docs.receitafederal.gov.br/apuracao-cbs/

---

**Aviso:** ferramenta interna de apoio; não substitui escrituração, consulta oficial, certidão, análise contábil ou autorização de pagamento.
