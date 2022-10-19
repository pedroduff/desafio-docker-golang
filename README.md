# Desafio Docker Golang

https://hub.docker.com/r/devduff/fullcyclerocks

docker pull devduff/fullcyclerocks


# O que foi feito

Realizei de duas formas: Em resumo, primeira forma fiz por partes, gerei um docker com a imagem golang e compilei o programa, após isso inseri em uma nova imagem. 
A outra forma seria fazer tudo isso pelo dockerfile, incluindo o arquivo do programa
que irá ser compilado

Abaixo segue o passo a passo de cada um:

Primeira forma:

1. Rodei um docker com a imagem golang com o objetivo de criar o código com o output Full Cycle Rocks.
docker run -it -v $(pwd)/golang:/go/src/fullcyclerocks golang bash 

2. Dentro do container fiz o seguintes passos:
    apt-get update
    apt-get install nano
    nano fullcyclerocks.go
        Dentro do arquivo coloquei o seguinte programa
        package main

        import "fmt"

        func main() {
            fmt.Println("Full Cycle Rocks")
        }
    go build fullcyclerocks.go
    ./fullcyclerocks

Já criamos o arquivo que precisamos rodar dentro da nossa imagem.

Agora para criarmos a imagem proposta, precisaremos criar um dockerfile com a imagem mais simples: scratch. (Dockerfile.old)
Copiarmos o arquivo executável de go para dentro do nossa imagem e,
Realizar o comando para rodar esse executável (Escrito no dockerfile)
Realizar o build da imagem

docker build -t devduff/fullcyclerocks .

Após isso subirmos a imagem para o dockerhub 

Segunda forma (mais simples):
Foi criado tudo através do dockerfile -> olhar Dockerfile.prod
docker build -t devduff/fullcyclerocks .



Para subir a imagem no dockerhub

docker pull devduff/fullcycleroks:latest

https://hub.docker.com/r/devduff/fullcyclerocks