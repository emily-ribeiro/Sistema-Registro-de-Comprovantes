# Sistema de Lançamentos - Eixo Barretos 📊

Um sistema web ágil e responsivo desenvolvido para o registo, gestão e consolidação de comprovativos de pagamento da Sede Mundial (Eixo Barretos). A aplicação permite o envio de dados e imagens diretamente para o Google Drive, mantendo a rastreabilidade e a organização dos documentos financeiros em nuvem.

## 🚀 Funcionalidades

* **Registo de Lançamentos:** Preenchimento de dados financeiros com preenchimento automático do Pastor e Telefone com base no "Campo" (Cidade) selecionado.
* **Upload em Nuvem:** Envio automático de fotos e PDFs dos comprovativos diretamente para pastas organizadas dinamicamente no Google Drive.
* **Rastreabilidade e Padronização:** Os ficheiros são renomeados automaticamente no Drive seguindo o padrão: `Data - Campo (Pastor) - Valor.extensão`.
* **Exclusão Sincronizada:** Ao apagar um registo na interface, o ficheiro correspondente é movido automaticamente para a lixeira do Google Drive, garantindo a integridade dos dados.
* **Geração de Relatórios:** Consolidação dos dados inseridos numa tabela e exportação direta para PDF (formato paisagem), ideal para fecho de mês em desktop.

## 🛠️ Tecnologias e Arquitetura

O projeto foi construído com uma arquitetura *Serverless* (sem servidor tradicional), dividida em duas camadas:

**Frontend (Interface do Utilizador):**
* **HTML5, CSS3 e JavaScript (Vanilla):** Estruturação, estilização responsiva e lógica de negócio.
* **html2pdf.js:** Biblioteca para conversão do relatório HTML em documento PDF.
* **GitHub Pages:** Hospedagem contínua e gratuita da interface web.

**Backend & Storage (API e Armazenamento):**
* **Google Apps Script (GAS):** Funciona como uma API REST (recebendo requisições `POST` com JSON) para processar os uploads e as exclusões.
* **Google Drive:** Atua como o banco de dados e servidor de ficheiros, criando subpastas automaticamente e gerando links de visualização.

## ⚙️ Como Utilizar / Testar

1.  Acesse a aplicação online: [**[](https://github.com/emily-ribeiro/Sistema-Registro-de-Comprovantes.git/index.git)**]
2.  Preencha a data e o valor do lançamento.
3.  Selecione a cidade correspondente no campo **Campo**. O sistema preencherá automaticamente os dados do responsável.
4.  Faça o upload de uma imagem ou PDF de teste e clique em "Adicionar Lançamento".
5.  O registo aparecerá na tabela. Pode clicar em "Abrir Anexo" para ver o ficheiro hospedado no Google Drive ou clicar em "Excluir" para testar a remoção sincronizada.
6.  *(Para testes em Desktop)* Clique no botão "Gerar Relatório em PDF" para exportar a tabela consolidada.

## 🛡️ Qualidade e Segurança

* **Validação de Inputs:** Campos bloqueados (`readonly`) e tipagem rigorosa para evitar falhas humanas na digitação de responsáveis.
* **Tratamento de Exceções:** Bloqueio de submissões duplicadas (`disabled state` com `loading`) e alertas de erro para garantir feedback claro ao utilizador em caso de falhas na rede.
* **Isolamento de Credenciais:** O código do Google Apps Script que possui as permissões de escrita no Drive roda exclusivamente nos servidores da Google, não expondo IDs ou chaves sensíveis no código do frontend público.