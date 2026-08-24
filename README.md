<?php

class Livro {
    public string $titulo;
    public string $autor;
    public bool $disponivel;
    
    public function __construct(string $titulo, string $autor){
        $this->titulo = $titulo;
        $this->autor = $autor;
        $this->disponivel = true;
    }
    
    public function emprestar(): void{
        if ($this->disponivel){
            $this->disponivel = false;
    }
    else {
            echo "Erro: O livro '{$this->titulo}' já está emprestado.\n";
        }
    }
    
    public function devolver(): void{
        $this->disponivel = true;
    }
}

$titulo = readline("Coloque o titulo: \n");
$autor = readline("Coloque o autor: \n");

$livro = new Livro($titulo, $autor);

do {
    echo "\n=== Menu de Opções ===\n";
    echo "1. Verificar status\n";
    echo "2. Emprestar livro\n";
    echo "3. Devolver livro\n";
    echo "4. Sair\n";
        
    $opcao = readline("Escolha uma opção: ");
    echo "\n";

    switch ($opcao) {
        case '1':
            $status = $livro->disponivel ? "Disponível" : "Emprestado";
            echo "Status atual de '{$livro->titulo}': {$status}\n";
            break;
        case '2':
            $livro->emprestar();
            break;
        case '3':
            $livro->devolver();
            break;
        case '4':
            echo "Saindo do sistema de biblioteca. Até logo!\n";
            break;
        default:
            echo "Opção inválida. Tente novamente.\n";
    }
} while ($opcao !== '4');

