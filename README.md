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


<?php

class Retangulo{
    private float $largura;
    private float $altura;
    
    public function __construct(float $largura, float $altura){
        $this->largura = $largura;
        $this->altura = $altura;
    }

    public function calcular_area(): float{
    return $this->largura * $this->altura;
    }
    
    public function calcular_perimetro(): float{
        return 2 * ($this->largura + $this->altura);
    }
    
    public function isQuadrado(): bool{
        return $this->altura == $this->largura;
    }
}

$larguraDigitada = (float) readline("Coloque a largura: \n");
$alturaDigitada = (float) readline("Coloque a altura: \n");

$retangulo = new Retangulo($larguraDigitada, $alturaDigitada);

echo ("A área é: ". $retangulo->calcular_area(). "\n");
echo("O perimetro é: ". $retangulo->calcular_perimetro(). "\n");
echo("É um quadrado? ". ($retangulo->isQuadrado() ? "Sim":"Não"). "\n")

<?php

class AcessoSistema
{
    private static int $totalAcessos = 0;

    public function __construct()
    {
        self::$totalAcessos++;
    }

    
    public static function getTotalAcessos(): int
    {
        return self::$totalAcessos;
    }
}

$acesso1 = new AcessoSistema();
$acesso2 = new AcessoSistema();
$acesso3 = new AcessoSistema();
$acesso4 = new AcessoSistema();

echo "Total de acessos: " . AcessoSistema::getTotalAcessos();

<?php
class Lampada {
    private bool $ligada = false;

    public function ligar(): void {
        $this->ligada = true;
    }

    public function desligar(): void {
        $this->ligada = false;
    }

    public function observar(): string {
        if ($this->ligada) {
            return "A lâmpada está ligada";
        }
        return "A lâmpada está desligada";
    }
}

<?php

class ContaBancaria {
    private string $titular;
    private float $saldo;

    public function __construct(string $titular, float $saldoInicial) {
        $this->titular = $titular;
        $this->saldo = $saldoInicial >= 0 ? $saldoInicial : 0.0;
    }

    public function depositar(float $valor): void {
        if ($valor > 0) {
            $this->saldo += $valor;
        }
    }

    public function sacar(float $valor): void {
        if ($valor > 0 && $valor <= $this->saldo) {
            $this->saldo -= $valor;
        }
    }

    public function getSaldo(): float {
        return $this->saldo;
    }

    public function getTitular(): string {
        return $this->titular;
    }
}


$conta = new ContaBancaria("Carlos Silva", 500.00);
$conta->depositar(250.50);
$conta->sacar(150.00);
$conta->sacar(900.00);
