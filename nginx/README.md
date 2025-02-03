# NGINX + NODE/VUE.JS

Este repositório contém Dockerfiles úteis para diferentes propósitos, incluindo a construção e o serviço de aplicações Vue.js com Nginx.

---

### Dockerfile: `build` (`Dockerfile.Build&Nginx`)

Este Dockerfile é projetado para construir uma aplicação Vue.js e servi-la usando Nginx. Ele utiliza uma abordagem de múltiplos estágios para otimizar o processo de construção e implantação.

#### Key Features:
- **Build Stage**:
  - **Base Image**: Utiliza `node:20` como imagem base para a construção da aplicação.
  - **Working Directory**: Define o diretório de trabalho como `/app`.
  - **Dependency Installation**: Copia `package.json` e `yarn.lock` e instala as dependências usando `yarn install`.
  - **Source Code**: Copia o restante do código-fonte da aplicação.
  - **Build Process**: Executa `yarn build` para construir a aplicação Vue.js.

- **Production Stage**:
  - **Base Image**: Utiliza `nginx:1.21-alpine` como imagem base para servir a aplicação.
  - **Copy Built Files**: Copia os arquivos construídos do estágio de construção para o diretório Nginx.
  - **Custom Nginx Configuration**: Remove a configuração padrão do Nginx e copia uma configuração personalizada.
  - **Expose Port**: Expõe a porta 80 para servir a aplicação.
  - **Start Nginx**: Inicia o servidor Nginx.

#### Use Cases:
- Construção e serviço de aplicações Vue.js em um ambiente otimizado.
- Separação clara entre os estágios de construção e produção para melhorar a segurança e a eficiência.

---

### Dockerfile: `nginx` (`Dockerfile.nginx`)

Este Dockerfile é projetado para servir uma aplicação estática usando Nginx. Ele assume que os arquivos estáticos já foram construídos e estão prontos para serem servidos.

#### Key Features:
- **Base Image**: Utiliza `nginx:1.21-alpine` como imagem base.
- **Copy Static Files**: Copia os arquivos estáticos construídos para o diretório Nginx.
  - **Custom Nginx Configuration**: Copia uma configuração personalizada do Nginx.
  - **Expose Port**: Expõe a porta 80 para servir a aplicação.
  - **Start Nginx**: Inicia o servidor Nginx com o comando `daemon off`.

#### Use Cases:
- Servir aplicações estáticas em um ambiente leve e eficiente.
- Utilização em ambientes de produção onde os arquivos estáticos já foram construídos.

---