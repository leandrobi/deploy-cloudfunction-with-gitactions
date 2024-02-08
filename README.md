# Configurando Actions para Deploy do Google Cloud Function

Este guia fornece instruções passo a passo sobre como configurar integração contínua e implantação automática usando GitHub Actions e Google Cloud Platform (GCP) para automatizar o processo de implantação de Cloud Functions.


## Criando uma Chave JSON no Google Cloud Platform (GCP)

1. Acesse o [Console do Google Cloud Platform](https://console.cloud.google.com/).
2. No painel de navegação, clique no menu de hambúrguer (três linhas no canto superior esquerdo) e vá para "IAM e administração" > "Contas de serviço".
3. Selecione o projeto no qual deseja criar a chave.
4. Na página "Contas de serviço", clique em "Criar conta de serviço".
5. Preencha o nome da conta de serviço e clique em "Criar".
6. Na seção "Papéis", atribua as permissões necessárias à conta de serviço (por exemplo, "Cloud Functions Developer").
7. Clique em "Continuar" e depois em "Concluir" para criar a conta de serviço.
8. Na lista de contas de serviço, encontre a conta que você acabou de criar e clique nela.
9. Na página da conta de serviço, clique em "Adicionar chave" > "Criar nova chave".
10. Selecione o tipo de chave como JSON e clique em "Criar".
11. Um arquivo JSON com sua chave de serviço será baixado para o seu computador. Guarde este arquivo com segurança.
12. Certifique-se de que o serviço run.googleapis.com esteja habilitado em seu projeto no Google Cloud Platform. Você pode habilitá-lo acessando o Console do GCP, navegando até a seção "APIs e Serviços" e ativando o serviço Cloud Run API, que é o serviço por trás das Cloud Functions. Ative o Cloud Functions API também.

## Configurando a Chave no GitHub

1. Acesse as configurações do seu repositório no GitHub.
2. Vá para a seção "Settings" (Configurações) do seu repositório.
3. Na seção "Secrets and variables" (Segredos), clique em "Actions" e depois em "New repository secret" da aba Secrets.
4. Nomeie o segredo como "GCP_SA_KEY" e cole o conteúdo da sua chave de serviço do Google Cloud Platform em "Value" (Valor).
5. Nomeie outro segredo como "GCP_PROJECT_ID" e informe o project-id do seu projeto GCP.
6. Clique em "Add secret" (Adicionar segredo) para salvar.

## Criando um Snippet no VSCode

1. Abra o VSCode e navegue até o arquivo que deseja criar um snippet.
2. Pressione `Ctrl+Shift+P` (ou `Cmd+Shift+P` no macOS) para abrir a paleta de comandos.
3. Digite "Preferences: Configure User Snippets" e pressione Enter.
4. Escolha o tipo de arquivo para o qual deseja criar o snippet (por exemplo, "Python").
5. Selecione a opção "New Global Snippets file" (Novo arquivo de snippets global).
6. Cole o snippet desejado no arquivo e salve-o.

## Configurando o Arquivo .yml no Projeto

1. Dentro do seu repositório no GitHub, navegue até o diretório `.github/workflows`.
2. Se não existir, crie um novo diretório chamado `workflows`.
3. Dentro do diretório `workflows`, crie um novo arquivo chamado `deploy.yml`.
4. Cole o conteúdo YAML do fluxo de trabalho de implantação no arquivo `deploy.yml`.
5. Adicione e comite as alterações no seu repositório do GitHub.

Com esses passos, você terá configurado a chave de serviço no GitHub, criado um snippet no VSCode e configurado o arquivo `.yml` no projeto do GitHub para o GitHub Actions. Isso permitirá que você automatize a implantação de suas Cloud Functions no Google Cloud Platform.
