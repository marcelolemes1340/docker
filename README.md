Pré-requisitos

    Docker instalado (https://docs.docker.com/get-docker/)

Construindo a Imagem

    docker build -t seu-nome-de-imagem .

Executando o Contêiner

    docker run -d -p 8080:8080 seu-nome-de-imagem

Dockerfile:

    Imagem Base:
        FROM ubuntu:22.04: Esta linha especifica a imagem base para seu contêiner. Estamos usando a imagem Ubuntu 22.04 leve como ponto de partida.

    Instalar Dependências:
        RUN apt-get update && apt-get install python3 python3-dev python3-pip -y: Esta linha atualiza as listas de pacotes e instala Python 3, cabeçalhos de desenvolvimento e o gerenciador de pacotes pip3 dentro do contêiner. O sinalizador -y garante a aceitação automática de quaisquer solicitações durante a instalação.

    Diretório de Trabalho:
        WORKDIR /app: Esta linha define o diretório de trabalho dentro do contêiner como /app.

    Copiar Código da Aplicação:
        COPY . .: Esta linha copia todos os arquivos e diretórios do diretório atual (onde o Dockerfile está localizado) para o diretório /app dentro do contêiner. Isso garante que seu código de aplicação esteja disponível dentro do contêiner.

    Instalar Dependências Python:
        RUN pip3 install --no-cache-dir -r requirements.txt: Esta linha instala as dependências Python listadas em um arquivo chamado requirements.txt (que é assumido estar localizado no diretório do seu projeto) usando o gerenciador de pacotes pip3. O sinalizador --no-cache-dir evita o download de pacotes do cache, garantindo uma instalação nova com os requisitos mais recentes.

    Expor Porta:
        EXPOSE 8080: Esta linha expõe a porta 8080 dentro do contêiner. Isso permite que sua aplicação escute nesta porta, potencialmente para uma interface web ou outra comunicação de rede.

    Comando Padrão:
        CMD [ "python3", "app.py" ]: Esta linha especifica o comando padrão a ser executado quando o contêiner iniciar. Neste caso, ele executa python3 app.py, o que assume que sua aplicação Python está no diretório /app e se chama app.py.
