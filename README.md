# NPM

## Iniciando um projeto

```bash
npm init
```

## Atualizar npm

```bash
npm install npm@latest -g
```

## Buscando pacotes

```bash
npm search <nome-pacote>
```

## Listar versões do pacote

```bash
npm show <nome-pacote@*.*.*>
```

## Instalando pacotes

```bash
npm install <nome-pacote>
```

Para instalar multiplos pacotes ao mesmo tempo é necessário que cada nome de pacote seja separado por um espaço

```bash
npm install <nome-pacote> [<nome-pacote> ...]
```

É possivel tambem instalar pacotes de repositórios git, utilizando a url do repositório, porem ele não permanece um versionamento pela versão.
Tambem pode ser adicionado pacotes do github, bitbucket, gitlab, etc.

```bash
npm install <url-repositorio-git>
# npm install https://github.com/jashkenas/underscore.git
```

Para instalar versões especificas de um pacote, deve-se adicionar o @ depois de seu nome com a versão desejada

```bash
npm install <nome-pacote[@nome-versao]>
```

Além de especificarmos a versão exata que queremos podemos adicionar informações diferenciadas

```bash
# versão maior ou igual que a descrita
npm install <nome-pacote[@>nome-versao]>

# versão maior que e menos que
npm install <nome-pacote[@>nome-versao <nome-versao]>

# para instalar a versão mais nova de uma pacote
npm install <nome-pacote[@latest]>
```

Caso queira adicionar o pacote como dependencia de desenvolvimento, deve-se adicionar o parâmetro --save-dev ou -D

```bash
npm install [--save-dev] <nome-pacote>

npm install [-D] <nome-pacote>
```

Pacotes podem ser adicionados globalmente, assim ficando disponivel em qualquer diretório que você esteja, usado principalmente para pacotes CLI, sendo necessário adicionar o parâmetro -g na hora da instalação do pacote

```bash
npm install [-g] <nome-pacote>
```

Comando mais compacto

```bash
npm i [-D] [-g] <nome-pacote>
```

## Fazer download dos pacotes do package.json

```bash
npm install
```

## Atualização de pacotes

Para verificar os pacotes que estão desatualizados podemos utilizar o comando

```bash
npm outdated [-g]
```

Para verificar pacotes desatualizar sem recursão, deve-se utilizar o seguinte comando, assim com o depth ele ira verificar somente as dependencias "pais"

```bash
npm outdated -g --depth=0
```

Para atualizar todos os pacotes é utilizado o comando

```bash
npm update [-g] [<nome-pacote[@nome-versao]> [<nome-pacote[@nome-versao]> ...]]
```

Para forçar uma atualização de uma pacote mesmo com os prefixos de limitação de versão, usa-se o comando:

```bash
npm install <nome-pacote@nome-versao>
```

## Desinstalando pacotes

```bash
npm uninstall [-g] <nome-pacote> [<nome-pacote> ...]
```

## Remover pacotes não listados no package.json

Se houver uma variável de ambiente que identifica o ambiente como de produção, ele poderá remover as dependências de desenvolvimento (devDependencies)

```bash
npm prune
```

## Descobrindo o diretório dos pacotes globais do npm

```bash
npm config get prefix
```

## Listando pacotes

```bash
npm ls [-g] --depth=0
```

## Criar uma conta no npm

```bash
npm adduser
```

## Realizar login da sua conta

```bash
npm login
```

## Realizar logout da sua conta

```bash
npm logout
```

## Exibir nome do usuário logado

```bash
npm whoami
```

## Publicar o pacote npm

```bash
npm publish
```

Caso haja algum arquivo como .gitignore ou .npmignore eles farão efeito no que será enviado para o pacote publicado

## Remover pacote publicado

```bash
npm unpublish
```

## Marcar pacote como obsoleto

```bash
npm deprecate
```

## Versão do pacote npm

```bash
# formato major.minor.path, seguindo padrão de versionamento
npm version path||minor||major
```

Após atualizar a versão, utilizar o comando de publicação de pacote npm

```bash
npm publish
```

## Valores padrões para o package.json

```bash
# mudar para a pasta raiz e criar um arquivo .npm-init.js igual ao deste repositório
cd ~
# rodar o npm init
npm init
```

O arquivo .npm-init.js deve conter a seguinte sintax dentro dele:

```javascript
module.exports = {
  "meucampo": "meuvalor"
}
```

## Simbolos de versão do package.json

Seguindo o sistema de versões major.minor.patch:

* ^: Somente versões que alterem o path e minor
* ~: Somente versões que alterem o minor
* \>: Versões maiores que a descrita no package.json
* \>=: Versões maiores ou igual que a descrita no package.json
* <: Versões menores que a descrita no package.json
* <=: Versões menores ou igual que a descrita no package.json
* (sem prefixo): Versão descrita no package.json

## Campo scripts no package.json

É utilizado para criar comandos utilitários para desenvolvimento da aplicação.
Para chama-los utiliza-se o comando

```bash
# quando os nomes dos scripts são test ou start
npm <nome-script>
# quando o nome é diferente
npm run <nome-script>
```

## Configurações de comportamento do npm via arquivo

As configurações são realizadas atravez do arquivo .npmrc armazenado no diretório raiz (cd ~).
Estas configurações podem alterar padrões do npm como o prefixo das dependencias (^, ~, >, <, etc), diretório global, e muitas outras configurações

```bash
# listagem de valores do arquivo
npm config list
# adicionar valor ao arquivo
npm config set <nome-campo> <valor-campo>
# pegar valor do arquivo
npm config get <nome-campo>
# remover valor do arquivo
npm config delete <nome-campo>
# abrir arquivo em um editor de texto
npm config edit
# comando encurtado
npm c
```

## Comandos para cache do npm

```bash
# adicionar ao cache
npm cache add <arquivo||diretorio||pacote-nome@nome-versao>
# limpar cache
npm cache clean [<item-com-cache>]
# verifica cache não utilizado
npm cache verify
```

## Abrir link do campo repository do package.json

```bash
npm repo
```

## Gerenciar configurações e variáveis de ambiente

```bash
# comandos especificos devem ser verificados na documentação do npm (comando npm config precisa de mais parâmetros)
npm config
```

## Hooks (observable)

São nomes de scripts que são executados automaticamente baseado na ação que ocorre, são eles:

* prepublish: Executado antes do pacote ser empacotado e publicado.
* prepare: Executado antes e após do pacote ser empacotado e publicado.
* prepublishOnly: Executado antes do pacote estar preparado e empacotado, apenas com "npm publish"
* prepack: Executado antes de um empacotamento (npm pack e npm publish)
* postpack: Executado após os tarball serem gerados e movidos para seu destino
* publish, postpublish: Executado após o pacote ter sido publicado com "npm publish"
* preinstall: Executado antes do pacote ter sido instalado com "npm install"
* install, postinstall: Executado após o pacote ter sido instalado com "npm install"
* preuninstall, uninstall: Executado antes do pacote ter sido desinstalado com "npm uninstall"
* postuninstall: Executado após o pacote ter sido desinstalado com "npm uninstall"
* preversion: Executado antes da mudança de versão com "npm version"
* version: Executado após a mudança de versão com "npm version", antes do commit
* postversion: Executado após a mudança de versão com "npm version", após o commit
* pretest, test, posttest: Executados com o comando "npm test"
* prestop, stop, poststop: Executados com o comando "npm stop"
* prestart, start, poststart: Executados com o comando "npm start"
* prerestart, restart, postrestart: Executados com o comando "npm restart". "npm restart" executará os scripts "stop" e "start" caso um script "restart" não seja fornecido
* preshrinkwrap, shrinkwrap, postshrinkwrap: Executados com o comando "npm shrinkwrap"

## Ajuda do npm

```bash
npm help
```