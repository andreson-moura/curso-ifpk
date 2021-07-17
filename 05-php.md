- [Introdução](#introdução)
- [Instalação](#instalação)
  - [Instalação no Linux](#instalação-no-linux)
  - [Instalação no Windows](#instalação-no-windows)
  - [Teste de Instalação](#teste-de-instalação)
- [Inicializando o servidor builtin do PHP](#inicializando-o-servidor-builtin-do-php)
- [Inicializando o PHP](#inicializando-o-php)
- [Variáveis](#variáveis)
- [Interagindo com o usuário](#interagindo-com-o-usuário)
- [Estruturas de Decisão](#estruturas-de-decisão)
- [Funções](#funções)
- [Criando Funções](#criando-funções)
- [Trabalhando com Arrays](#trabalhando-com-arrays)
  - [for](#for)
  - [while](#while)
  - [do... while](#do-while)
  - [foreach](#foreach)
- [Orientação a Objetos](#orientação-a-objetos)
  - [Classe](#classe)
  - [Objeto](#objeto)
  - [Métodos](#métodos)
  - [Atributos](#atributos)
  - [Encapsulamento](#encapsulamento)
  - [Acessando métodos e atributos do objeto](#acessando-métodos-e-atributos-do-objeto)
  - [Método Construtor](#método-construtor)
- [Transcrevendo classes](#transcrevendo-classes)
- [Inclusão de Scripts PHP](#inclusão-de-scripts-php)
  - [include()](#include)
  - [require()](#require)
  - [include_once() e require_once()](#include_once-e-require_once)
- [Composer](#composer)
  - [Instalação no Windows](#instalação-no-windows-1)
  - [Instalação no Linux](#instalação-no-linux-1)
  - [Verificando instalação](#verificando-instalação)
  - [Instalação de Pacotes](#instalação-de-pacotes)
    - [Instalando o DomPDF](#instalando-o-dompdf)
    - [Utilizando o autoload](#utilizando-o-autoload)
    - [Gerando um PDF](#gerando-um-pdf)


# Introdução

PHP é uma linguagem de programação utilizada por programadores e desenvolvedores para construir sites dinâmicos, extensões de integração de aplicações e agilizar no desenvolvimento de um sistema. 

Linguagens de script podem rodar tanto do lado do servidor (backend) quanto do lado do cliente (frontend).

Scripts do tipo frontend são processados pelos navegadores. Quando o seu browser – também conhecido como o cliente – solicita uma página contendo scripts do lado do cliente, o servidor responde enviando os códigos-fontes que são executáveis pelo navegador.

Por outro lado, linguagem de scripts do tipo backend significam que esses scripts são executados nos servidores antes de serem enviados ao navegador. Então ao invés de mandar o código-fonte, os servidores da web processam (parse) os códigos antes ao transformá-los num formato HTML puro.

# Instalação

## Instalação no Linux

Para instalação no Linux você precisa executar o seguinte comando:

````sh
sudo apt update && sudo apt install php7.4
````

## Instalação no Windows

Para a instalação no Windows você pode instalar especificamente o PHP, porém, muito comum, é possível instalar pacotes prontos para desenvolvimento web, como serviços como nginx, apache, mysql e etc. embutidos. 

No nosso curso nós sugerimos a instalação via [Laragon - Full](https://laragon.org/download/index.html). A instalação é bem simples: next, next, install. Após a instalação do Laragon é necessário atualizar as variáveis de ambiente. 

Com o Laragon aberto vá em ``Menu`` > ``Ferramentas`` > ``Variáveis de ambiente no Path`` > ``Add Lagon to Path``

## Teste de Instalação

Tanto no Windows quanto no Linux, abra o terminal e execute o seguinte comando:

````sh
php -v
````

Se foi retornado a versão do PHP, então a instalação ocorreu corretamente. Será algo simular ao abaixo:

````sh
PHP 7.4.19 (cli) (built: May 4 2021 14:24:36) (ZTS Visual C++ 2017 x64)
Copyright (c)  The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
````

Se o comando retornou algo similar a isso, você está pronto para utilizar o PHP.

# Inicializando o servidor builtin do PHP

A partir da versão 5 do PHP, o PHP vem com um servidor HTTP desde a sua instalação. Não sendo necessário o uso do apache ou do nginx em ambiente de desenvolvimento. Para inicializar o servidor builtin do PHP, entre na sua pasta de projetos, crie um novo projeto, crie um arquivo ``index.php`` e execute o comando ``php -S localhost:8000``. Da seguinte forma:

````sh
cd ~/Projetos

mkdir php

cd php

touch index.php

php -S localhost:8000

````

A mensagem que deverá aparecer será a seguinte:

````sh
PHP 7.4.19 Development Server (http://localhost:8000) started
````

Para parar o servidor você deve apertar as teclas ``CTRL`` + ``C``. 

# Inicializando o PHP

Ao acessar ``http://localhost:8000`` você estará acessando o arquivo ``index.php`` que está dentro da pasta do seu projeto. Você deverá inserir a tag de inicialização do php (``<?php``) dentro deste arquivo. Portanto o conteúdo do arquivo deverá ser:

````php
<?php

// CÓDIGO PHP AQUI
````

# Variáveis

Para declaracar variáveis no PHP você deve usar o ``$`` na frente do nome da variável.

````php
$meuValor = 0;
$meuNome = "João Pereira da Silva";
````

# Interagindo com o usuário

Para exibir informações para o usuário você deverá usar o comando echo. Lembre-se sempre de utilizar palavras reservadas do php em letras minusculas.

````php

$minhaIdade = 2021 - 1992;
echo "Minha idade é: " . $minhaIdade; // Concatenação de strings é feita através de um ponto

````

> No PHP não deve esquecer o ponto e vírgula no final de cada instrução

# Estruturas de Decisão

As estruturas de decisão do PHP são bem semelhantes àquelas que vimos na nossa aula de lógica de programação.

````php
$anoNascimento = 1992;
$idade = 2021 - 1992;

if ($idade >= 18) {
    echo "Você é maior de idade";
} else {
    echo "Você é menor de idade;
}
````

# Funções

Algumas das funções mais utilizadas no PHP e sua utilidade:

````php
echo date('d/m/Y'); // Retorna o dia atual no formato passado no parâmetro
echo date('d/m/Y H:i:s'); // Retorna o dia e hora atual
echo strlen("Hello world!"); // Tamanho de uma string
echo substr("abcdef", 0, 3);  // Recorta um pedaço da string
print_r([1, 2, 3]); // Imprime informação sobre uma variável de forma legível
print_r(explode(",", "3,6,5,ab")); // Quebra a string em arrays por um separador
echo str_replace("a", "e", "casa"); // Substituti um valor dentro de uma string por outro
echo strtolower("ADELITON"); // Transforma todas as letras para minúsculo
echo strtoupper("adeliton"); // Transforma todas as letras para maiusculo
echo trim("  ADÉLITON "); // Elimina os espaços em branco no início e no fim da string
echo file_get_contents("arquivo.txt"); // Retorna o conteúdo de um arquivo
echo json_encode(["meuArray" => 1, "teste" => 2]); // Cria um json a partir de um array
echo json_decode('{ "bar": "baz" }'); // Transforma um json em um array
echo strtotime("tomorrow"); // Interpreta qualquer descrição de data/hora em texto em inglês em timestamp Unix
````

Todas as funções, assim como exemplos e documentação em português, estão disponíveis na [documentação oficial do PHP](https://www.php.net/manual/pt_BR/).

# Criando Funções

A criação de função é muito semelhante àquela trabalhada por nós no módulo de lógica de programação.

````php
function calcularIdade() {
  $anoAtual = 2021;
  $anoNascimento = 1992;
  $idade = $anoAtual - $anoNascimento;
  
  echo "Sua idade em " . $anoAtual . " é " . $idade . " anos.";
}

calcularIdade();
````

# Trabalhando com Arrays

## for

A instrução for cria um loop que consiste em três expressões opcionais, dentro de parênteses e separadas por ponto e vírgula, seguidas por uma declaração ou uma sequência de declarações executadas em sequência.

````php
for ($i = 0; $i < 9; $i++) {
   echo $i;
}
````

## while
A declaração while cria um laço que executa uma rotina especifica enquanto a condição de teste for avaliada como verdadeira. A condição é avaliada antes da execução da rotina.

````php
$n = 0;
while ($n < 3) {
  echo $n;
  $n++;
}
````

## do... while

A declaração do...while cria um laço que executa uma declaração até que o teste da condição for falsa (false). A condição é avaliada depois que o bloco de código é executado, resultando que uma declaração seja executada pelo menos uma vez.

````php
$n = 3;
do {
  echo $n;
  $n++;
} while ($n < 3);
````

## foreach

O construtor foreach fornece uma maneira fácil de iterar sobre arrays. 

````php
$notas = [9, 8, 7, 8.6];

foreach ($notas as $nota) {
    echo $nota;
}
````

Caso eu queira acessar o valor do índice, eu devo fazer da seguinte forma:
````php
$notas = [10, 7, 6.7, 7.8];

foreach ($notas as $indice => $nota) {
    echo $indice . "/" . $nota;
}
````

# Orientação a Objetos

## Classe

Para a criação de uma classe no PHP, a sintaxe é a mesma que a utilizada no JavaScript.

````php
class Aluno
{
    // CONTEÚDO DA CLASSE AQUI
}
````

## Objeto

Para instanciar um objeto você deve utilizar a seguinte sintaxe:

````php
class Aluno 
{
    // CONTEÚDO DA CLASSE AQUI
}

$aluno = new Aluno();
````

## Métodos

A criação de métodos dentro de uma classe segue o mesmo padrão de criação de uma função comum.

````php
class Aluno
{
    function teste() 
    {
        echo "Você criou um método";
    }
}
````

## Atributos

A criação de atributo pode ser feita em qualquer lugar da classe, mas o recomendado é listar todos os atributos na declaração da classe

````php
class Aluno
{
    $nome;

    function teste()
    {
        echo "Você criou um método";
    }
}
````

## Encapsulamento

Assim como no JavaScript, é possível colocar métodos e atributos como público e como privado. Da seguinte forma

````php
class Aluno
{
    public $nome;
    private $idade;

    public function teste()
    {
        echo "Você criou um método público";
    }

    private function teste2()
    {
        echo "Você criou um método privado"; 
    }
}
````

## Acessando métodos e atributos do objeto

Para acessar métodos e atributos do objeto você deve usar o operador de objetos do PHP ``->``. Lembrando sempre que para acessar um objeto ou um atributo de dentro da classe você deve usar o ``this``.

````php
class Aluno
{
    public $nome = "Adéliton";
    private $idade;

    public function nome()
    {
        echo "Seu nome é: " . $this->nome;
    }

    public function idade()
    {
        echo "Sua idade é: " . $this->idade;
    }
}

$meuObjeto = new Aluno();
$meuObjeto->nome();
$meuObjeto->idade = 29;
$meuObjeto->idade();
````

## Método Construtor

No PHP o método construtor deve ser feito usando o ``__construct``, da seguinte forma:

````php
class Aluno 
{
    public function __construct()
    {
        // ESTE É O MÉTODO CONSTRUTOR
    }
}
````

# Transcrevendo classes

Vamos transcrever nossa classe criada no Projeto Prático de Lógica de Programação para o PHP

<details> 
  <summary>Clique para visualizar a classe</summary>

````php
class Aluno {
    private $notas = [];
    private $totalNotas = 0;

    public function __construct($nome, $anoNascimento)
    {
        $this->nome = $nome;
        $this->anoNascimento = $anoNascimento;
        $this->calculaIdade();
    }
  
    private function calculaIdade()
    {
        $this->idade = 2021 - $this->anoNascimento;
    }
  
    public function adicionaNota($nota)
    {
        if (count($this->notas) == 4) {
            echo "Você já adicionou quatro notas. Ignorando.";
        } else {
            array_push($this->notas, $nota);
        }
    }

    public function calculaMedia()
    {
        foreach ($this->notas as $nota) {
            $this->totalNotas += $nota;
        }

        $this->media = $this->totalNotas / count($this->notas);
    }
}

$alunos = [];

$aluno1 = new Aluno("Adéliton", 1992);
$aluno1->adicionaNota(8.9);
$aluno1->adicionaNota(9);
$aluno1->adicionaNota(5.5);
$aluno1->adicionaNota(7.8);
$aluno1->calculaMedia();
$alunos[] = $aluno1;

$aluno2 = new Aluno("João", 1995);
$aluno2->adicionaNota(5);
$aluno2->adicionaNota(7);
$aluno2->adicionaNota(8.3);
$aluno2->adicionaNota(3.4);
$aluno2->calculaMedia();
$alunos[] = $aluno2;

$aluno3 = new Aluno("Maria", 1992);
$aluno3->adicionaNota(10);
$aluno3->adicionaNota(9.5);
$aluno3->adicionaNota(8.9);
$aluno3->adicionaNota(9.1);
$aluno3->calculaMedia();
$alunos[] = $aluno3;

$aluno4 = new Aluno("Alberto", 1990);
$aluno4->adicionaNota(4.5);
$aluno4->adicionaNota(5.9);
$aluno4->adicionaNota(3.1);
$aluno4->adicionaNota(4.3);
$aluno4->calculaMedia();
$alunos[] = $aluno4;

$idadeMaisNova = 999;
$maiorMedia = 0;
$alunoMaisNovo = null;
$alunoMaiorMedia = null;

foreach ($alunos as $aluno) {
    if ($aluno->idade < $idadeMaisNova) {
        $idadeMaisNova = $aluno->idade;
        $alunoMaisNovo = $aluno;
    }

    if ($aluno->media > $maiorMedia) {
        $maiorMedia = $aluno->media;
        $alunoMaiorMedia = $aluno;
    }
}

echo "O aluno mais novo é: " . $alunoMaisNovo->nome;
echo "O aluno com a maior média é: " . $alunoMaiorMedia->nome; 

print_r($alunos);
````

</details>

# Inclusão de Scripts PHP

## include()

A função include() do PHP tem como objetivo incluir (como o próprio nome diz) um arquivo dentro do outro quando acessado. Caso ocorra algum problema na inclusão deste, será apresentado um Warning (aviso) que não foi possível incluir o arquivo e continuará a exibição da página normalmente sem a inclusão do arquivo. A função include() aceita parâmetros via GET quando chama um arquivo.

````php
    include('pages/footer.php');
````

## require()

A função require() do PHP tem a mesma funcionalidade da função include(), citada acima, com a diferença que se caso o arquivo que você está incluindo não exista (ou não seja encontrado), será gerado um Fatal Error (erro fatal), paralizando a execução de qualquer script que venha após a linha do require(); outra divergência é o fato desta função não aceitar parâmetros via GET para o arquivo chamado. Caso você utilize este parâmetro, ele será ignorado.

````php
    require('pages/footer.php');
````

## include_once() e require_once()
As funções include_once() e require_once() do PHP tem as suas funcionalidades praticamente “idênticas” às funções include() e require(), respectivamente. Digo “idênticas” (entre aspas) pois a única diferença entre elas é o fato da funções que possuem o “_once” só permitirem a inclusão do arquivo uma única vez na página e ignorando caso você chame ela mais vezes sem notar.

````php
    require('pages/footer.php');   
    include_once('pages/footer.php');
````

# Composer

O Composer é uma ferramenta para o gerenciamento de dependências em PHP. Ele permite que você declare as bibliotecas que seu projeto necessita e ele gerencia (instala / atualiza) elas para você.

Outra grande funcionalidade do composer é a possibilidade de fazer autoload de classes que utilizam o padrão PSR-4.

## Instalação no Windows

Basta [baixar o instalador](https://getcomposer.org/Composer-Setup.exe) e instalar como qualquer outro programa.

## Instalação no Linux

Execute os comandos abaixo exatamente na mesma ordem.

````sh
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

php composer-setup.php

php -r "unlink('composer-setup.php');"

sudo mv composer.phar /usr/local/bin/composer
sudo cp /usr/local/bin/composer /usr/bin/composerr
````

## Verificando instalação

Digite o comando abaixo e verifique se a versão 2 do Composer está instalada.

````sh
composer -V
````

O retorno tem que ser algo parecido com:

````sh
   ______
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 2.0.0 2019-02-11 10:52:10
````

## Instalação de Pacotes

Existem diversos pacotes, bibliotecas ou frameworks que podem ser instalados via composer. Esses projetos estão repositados no [Packagist.org](https://packagist.org/). Para nós entendermos como o Composer funciona, iremos fazer a instalação de um dos pacotes mais utilizados do PHP, o [DomPDF](https://github.com/dompdf/dompdf).

1. Primeiramente vamos entrar na nossa pasta de projetos
````sh
cd ~/Projetos/
````
2. Agora vamos criar uma pasta para o nosso novo projeto
````sh
mkdir composer
````
3. Vamos entrar na pasta criada e após isso inicializar o composer
````sh
cd composer

composer init
````
Você deverá responder as seguntes perguntas:

* **Nome do Pacote (Package Name)**: Dê um nome qualquer para o pacote.
* **Descrição (Description)**: Você pode deixar em branco.
* **Autor (Author)**: Você pode colocar seu nome precedido por seu email.
* **Versão Mínima Estável (Minimum Stability)**: Você pode deixar em branco.
* **Tipo do Pacote (Package Type)**: Você pode deixar em branco.
* **Licença (License)**: Deixe MIT.
* **Definir dependências (Define your dependencies)**: Digite ``no`` para essa pergunta, por enquanto.
* **Definir dependências dev**: Digite ``no`` para essa pergunta, por enquanto.
* **Adicionar PSR-4 (Add PSR-4)**: Digite ``n`` para pular.

Confirme as configurações e haverá um arquivo chamado ``composer.json`` dentro da pasta do seu projeto, persistindo todas as informações que você passou interativamente para o terminal. 

Agora já poderemos instalar os pacotes que precisamos dentro do nosso projeto. 

### Instalando o DomPDF

Primeiramente é bom visitar a página no GitHub do pacote que você deseja instalar. O DomPDF, por exemplo, está disponível [neste link](https://github.com/dompdf/dompdf). 

Para instalar um pacote no composer, você deve usar o comando ``composer require nome_do_usuario/nome_do_pacote``, no caso do dompdf o comando é o seguinte:

````sh
composer require dompdf/dompdf
````

Após executar o comando, o composer irá verificar se seu ambiente está apto para ter o pacote instalado. Como você pode ver [neste link](https://github.com/dompdf/dompdf/blob/master/composer.json), o dompdf também tem um arquivo ``composer.json`` onde ele dita suas dependências. No caso do dompdf, é requerido que a extensão ``ext-dom`` esteja instalada. Se você precisar instalar essa extensão no Linux, você deve utilizar o seguinte comando:

````sh
sudo apt install php-dom
````

Após isso você pode voltar a requerer o dompdf dentro do composer. 

### Utilizando o autoload

Ao baixar qualquer pacote utilizando o composer, o composer guarda o código fonte dele em uma pasta ``vendor`` dentro do seu projeto. Portanto, a classe principal do DomPDF já está no nosso projeto. 

````sh
ls ./vendor/dompdf/dompdf/src/Dompdf.php
````

Para que a gente não precise der include_once em cada classe baixada via composer, o composer possibilita que a gente inclua um único arquivo.

Então dentro de ``index.php``, apague tudo e inclua a seguinte linha:

````php
<?php

require_once './vendor/autoload.php';
````

### Gerando um PDF

Vamos gerar o nosso PDF. Agora que você já fez autoload das classes, é importante nós reiniciarmos nosso servidor (se você estiver com ele aberto). Para reiniciar, basta ir no terminal onde ele está aberto e apertar simultaneamente ``CTRL + C``, depois iniciar novamente ``php -S localhost:8000``.

Dentro de ``index.php`` deixe o seguinte código: (Extraído do manual de utilização do dompdf dentro do Github):

````php
<?php

require_once './vendor/autoload.php';

use Dompdf\Dompdf;

$dompdf = new Dompdf();
$dompdf->loadHTML("<h1>Meu HTML</h1>");
$dompdf->render();
$dompdf->stream("arquivo.pdf", ["Attachment" => false]);
````

Neste momento um PDF com o texto ``Meu HTML`` será exibido no seu navegador. 