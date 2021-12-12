# Andromeda

# Idioma/language

### Pegue um atalho/take a shortcut

* [Português](https://github.com/hexagonix/Distro#sistema-operacional-hexagonixandromeda)
* [English](https://github.com/hexagonix/Distro#hexagonixandromeda-operating-system)

<!-- Versão em português -->

# Sistema Operacional Hexagonix/Andromeda

Seja bem-vindo ao Sistema Operacional Hexagonix/Andromeda

## Notas de direitos autorais 

O Hexagonix/Andromeda foi desenvolvido do zero por [Felipe Lunkes](https://github.com/felipenlunkes).

Leia a [licença](LICENSE) para mais informações sobre direitos autorais, propriedade de código e redistribuição.

* Sistema Operacional Andromeda. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. Todos os direitos reservados.
* Kernel Hexagon. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. Todos os direitos reservados.
* Gerenciador de Boot Saturno. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. Todos os direitos reservados.
* Hexagon Boot (HBoot). Copyright © 2020-2022 Felipe Miguel Nery Lunkes. Todos os direitos reservados.

## Antes de mais nada

No final deste arquivo você encontra um tutorial para executar o Hexagonix/Andromeda em seu computador, tanto em uma versão virtualizada como de forma nativa. Lembre-se que é necessário possuir um computador de arquitetura x86 ou um emulador, caso esteja utilizando um dispositivo de outra arquitetura para testes. 

* [Documentação do sistema (em construção)](https://github.com/hexagonix/Distro/tree/main/Doc)

# Sobre o sistema

## Desenvolvimento

O Hexagonix/Andromeda e todos os seus componentes vêm sendo desenvolvidos desde 2015 e foram escritos completamente em linguagem Assembly.

## Por que dois nomes? Hexagonix e Andromeda, o quê são?

No início, o Andromeda foi planejado para ser um sistema operacional completo, composto pelo kernel, bibliotecas, interface gráfica e de texto e utilitários. Mais tarde, com o passar do tempo e a mudança na abordagem da arquitetura e objetivos do sistema, os componentes foram separados e se tornaram projetos independentes a nível de funcionamento, organização e desenvolvimento. Como será possível observar a diante, o núcleo do Andromeda foi separado do restante da árvore de código do Andromeda, se tornando um projeto independente, recebendo até um nome, Hexagon. A partir de então, surgiu a ideia de flexibilizar a composição do sistema e permitir o desenvolvimento de distribuições, como ocorre no GNU/Linux. Desta forma, distribuições do Hexagon poderiam ser criadas, agrupando os componentes necessários para o funcionamento básico (Hexagonix) e permitindo a extensão do sistema caso seja necessário, com novos componentes, módulos e utilitários, sendo o userland definido a cada caso. Com a mudança de arquitetura do próprio sistema, com o núcleo se aproximando de uma arquitetura semelhante ao Unix, novos utilitários no estilo e sintaxe Unix foram desenvolvidos e mantidos separados, em um outro projeto. Do projeto Andromeda original temos os aplicativos e bibliotecas gráficas específicas do Andromeda. Foi então criado um sistema base, que por si só já pode ser executado plenamente, e se transformou na base do Andromeda. Esse sistema base se chama Hexagonix, e é composto pelo carregador de inicialização HBoot, pelo kernel Hexagon, pelo shell, bibliotecas de ambiente Unix (aqui denominado ambiente Hexagonix) e utilitários Unix. Esse sistema é plenamente funcional, mas carece de recursos gráficos e aplicativos desenvolvidos para o ambiente Andromeda. Dessa forma, o Andromeda se destaca por ser uma camada a mais construída sobre a base do Hexagonix, com recursos gráficos, uma biblioteca gráfica e utilitários que funcionam sobre o Hexagonix e estendem sua função. Esse ambiente construído foi nomeado de ambiente Andromeda. Para suprir diferentes necessidades, as duas distribuições serão sempre mantidas. Ambas as versões são funcionais e podem ser utilizadas, dependendo do uso final desejado. Em resumo, tanto o Hexagonix quanto o Andromeda são distribuições do kernel Hexagon, diferindo quanto aos componentes incluídos.

Para compreender melhor esse modelo de distribuição, um exemplo adequado seria o que ocorre com o macOS (Apple)[^1]. O macOS é um sistema operacional Unix-like constrúido sobre o Darwin, um sistema operacional livre composto pelo kernel XNU, bibliotecas e utilitários, adicionando sobre o Darwin a interface gráfica Aqua e demais aplicativos e utilitários desenvolvidos pela Apple e outros fornecedores. O ambiente Darwin é facilmente acessado e observado através do macOS, como na utilização do terminal, por exemplo. O Darwin é um sistema completo e funcional, mas carece de alguns recursos gráficos, por exemplo, que só são distribúidos juntamente ao macOS. Nessa analogia, temos o macOS como Andromeda e Darwin como Hexagonix. 

[^1]: Você pode obter mais informações sobre a relação entre o Darwin e o macOS [aqui](https://pt.wikipedia.org/wiki/Darwin_(sistema_operacional)).

## E o código-fonte?

O código-fonte do projeto ainda não está disponível publicamente, mas há planos para a disponibilização no futuro. Entretanto, a distribuição das imagens de disco, tanto com o Hexagonix quanto com o Andromeda, é livre. Observe a [licença](LICENSE) disponível neste repositório para mais informações.

## O que é um sistema operacional?

O Sistema Operacional Hexagonix/Andromeda é uma coleção de peças de software que atua no gerenciamento do hardware do computador onde está instalado, permitindo o carregamento e funcionamento de aplicativos e a comunicação entre os diversos dispositivos conectados ao dispositivo. Ele é composto por vários componentes, que atuam no processo de inicialização do computador, testes de recursos e carregamento do kernel (núcleo) do sistema operacional, o núcleo, uma interface de interação com o usuário e uma série de utilitários.
Tanto o hexagonix quanto o Andromeda são distribuições que incorporam um kernel Unix-like, denominado Hexagon, bibliotecas de suporte, utilitários desenvolvidos exclusivamente para o ambiente Andromeda e utilitários Unix-like de linha de comando (estes últimos e o kernel Hexagon por si só já configuram um sistema operacional base, o Hexagonix).

## A história do Hexagonix/Andromeda:

O Andromeda começou como uma implementação em estrutura similar a sistemas do tipo DOS, com um interpretador com comandos internos com nomes, sintaxes e resultados semelhantes a um DOS genérico. O interpretador de comandos apresentava comandos de manipulação de arquivos e outros internamente, como em sistemas DOS convencionais. As unidades de disco também eram definidas como letras. Mais tarde, surgiu um interesse crescente e fascínio no funcionamento de sistemas Unix e todo o código foi reescrito ou adaptado para tornar o kernel do Sistema um kernel Unix-like. Todos os componentes do Sistema, assim como no DOS, eram mantidos em uma única árvore até então. Com a versão 1.5 do Andromeda, com nome de código "Unix-like", o kernel foi bastante modificado e reescrito para se adequar à filosofia Unix. As mudanças incluíram até mesmo a forma como os dispositivos eram tratados, com a escrita de uma camada de abstração de hardware com o gerenciamento de dispositivos como arquivos, além da adição das chamadas de sistema abrir(), fechar(), escrever() e ler(). Também foram escritos os utilitários base Unix, com a retirada de comandos do interpretador padrão, que foi reescrito para dar lugar a um shell Unix-like. Os camandos internos foram movidos para os utilitários, que passaram a contar com estrutura e sintaxe no estilo Unix. O restante dos utilitários, como mount, foi escrita, já tirando proveito da chamada abrir(), que também é utilizada para montar volume, além de abrir arquivos ordinários do volume. A chamada abrir() também é utilizada para iniciar outros periféricos, como portas seriais e paralelas. A chamada escrever() também funciona com dispositivos e arquivos, bem como fechar(). Foi também introduzido um VFS (Virtual File System), que suportará no futuro vários sistemas de arquivos e que torna transparente para o Sistema, programadores e usuários o gerenciamento de arquivos. Também foram incluídas novas funções de gerenciamento de hardware e muitos aprimoramentos e correções de bugs. O Sistema ganha novos utilitários Unix até o presente momento. Após essa alteração da proposta e arquitetura, os componentes foram separados e alocados em projetos específicos. A união destes componentes forma o sistema operacional. No caso do Hexagonix, temos o HBoot, Hexagon, shell, bibliotecas e aplicativos Unix, enquanto o Andromeda estende o Hexagonix, incorporando outras bibliotecas e aplicativos que as utilizam.

## Versionalização do Hexagonix/Andromeda:

O sistema operacional apresenta uma numeração de versão independente dos componentes associados. Cada componente, desde o gerenciador de inicialização, até um simples utilitário, recebem uma numeração de versão independente e que reflete seu estado de desenvolvimento. Um número de versão do Hexagonix/Andromeda apresenta três conjuntos de números divididos em três blocos separados por um caractere de ponto ".". O primeiro deles representa o número principal de versão e se baseia no número um. Já o segundo número se refere ao lançamento, este é o número que varia de um lançamento do Hexagonix/Andromeda para outro e distingue entre as grandes versões do Sistema, além de ser utilizado como número de versão que é verificado pelos aplicativos e utilitários para verificar se a versão do sistema apresenta os requisitos mínimos para a execução do software. Já o terceiro é o número de revisão de cada grande lançamento e, caso seja 0, pode ser omitido, ficando a versão com apenas dois blocos de algarismos. Um exemplo seriam as versões "1.14.4", cuja versão base é sempre 1, até o momento, 14 indica o lançamento (este se refere, na maioria das vezes, a real versão do Sistema. Pense, por exemplo, no sistema de numeração da Apple com o Mac OS X/OS X/macOS até a versão 11.0 Big Sur, que começa sempre com 10 e é seguido do número do lançamento e revisão). Já o número 4 seria a revisão dentro do grande lançamento, que diz respeito a correção de bugs e adição de alguma funcionalidade que não mude de forma profunda o Sistema nem o uso do mesmo.

Normalmente, o Hexagonix e o Andromeda apresentam a mesma numeração de versão principal, mas isso não é necessariamente obrigatório. Os números de versão podem divergir em algum momento, bem como os componentes de cada distribuição. A versão do Hexagon, por exemplo, pode ser diferente mesmo em números de versão idênticos, mas esse tipo de divergência será sempre evitada.

# Componentes do sistema

## Saturno

O primeiro componente do Hexagonix/Andromeda é o Saturno. Ele é responsável por receber o controle do processo de inicialização realizado pelo BIOS/UEFI e procurar no volume o segundo estágio de inicialização. Para isso, ele implementa um driver para leitura de um sistema de arquivos FAT16. O segundo estágio de inicialização (ver adiante) pode implementar drivers para outros sistemas de arquivos e é responsável por encontrar o Hexagon, carregar módulos HBoot ou carregar um sistema do tipo DOS compatível (versão BETA).

## Hexagon Boot (HBoot)

O Hexagon Boot (HBoot) é um componente desenvolvido permitir a inicialização do kernel Hexagon. Até então, a inicialização era realizada por apenas um estágio, que definia um ambiente bem básico, carregava o Hexagon na memória e imediatamente passava o controle para ele, fornecendo um conjunto bem pequeno e limitado de parâmetros, uma vez que o código desse estágio fica restrito a 512 bytes, o que limita a realização de diversos testes e processamento de dados. Como o HBoot, foi possível expandir o número de tarefas realizadas antes da execução do Hexagon, além da possibilidade de fornecer mais informações a respeito do ambiente da máquina e de inicialização. Isso é particularmente importante para permitir a criação de uma árvore de dispositivos que pode ser utilizada pelo Hexagon para decidir como manipular cada dispositivo identificado. O HBoot é capaz de verificar quais unidades de disco estão disponíveis na máquina, emitir um tom de inicialização, obter a quantidade de memória RAM disponível instalada e permitir ou não o seguimento do processo de boot de acordo com essa informação. Caso nenhuma interação do usuário seja detectada 3 segundos após todos os testes e atividades essenciais para criar um ambiente de inicialização para o Hexagon, o sistema irá carregar e executar o Hexagon (presente em um arquivo no volume nomeado de **HEXAGON.SIS**), sendo descarregado da memória. A interação com o HBoot se dá pelo pressionamento da tecla F8 após a respectiva mensagem surgir na tela. 

### Outras funções disponíveis

* O HBoot permite o carregamento de módulos no formato HBoot, que podem ser úteis, no futuro, para permitir testes de hardware, como testes de memória e disco, caso os módulos estejam disponíveis no disco. Os módulos podem ser utilizados também para extender as funções do HBoot. A especificação do formato já está disponível e um exemplo pode ser encontrado abaixo. Esses módulos podem ser utilizados para testar dispositivos específicos, obter informações do hardware ou carregar arquivos em sistemas de arquivos não suportados originalmente pelo HBoot.
* No contexto do desenvolvimento do Hexagonix, o HBoot também pode carregar diretamente, a partir de um módulo atualmente built-in (essa função será movida para um módulo standalone o quanto antes) o núcleo do sistema operacional de código livre FreeDOS[^2], para que ferramentas utilitárias já estabelecidas e robustas que sejam executadas em ambiente DOS possam ser executadas sobre o volume e arquivos Hexagonix/Andromeda. O FreeDOS foi escolhido devido a sua característica de kernel composto por um único arquivo, geralmente "KERNEL.SYS"[^3], além da sua distribuição livre e gratuita. Já outros DOS, como o MS-DOS, anterior a versão 7.0, utilizam dois arquivos que devem estar contíguos no disco, e isso não é possível aqui, visto que a instalação do FreeDOS ocorre já em um volume Hexagonix, com a cópia do kernel, interpretador de comando e outros utilitários DOS, sendo que o sistema operacional principal é o Hexagonix/Andromeda, com iniciação opcional do FreeDOS para alguma atividade em especial[^4]. Caso os componentes de sistema do FreeDOS não estejam presentes no disco (a cópia dos arquivos do FreeDOS não faz parte da imagem padrão), a inicialização em modo de compatibilidade DOS não irá ocorrer.

[^2]: Você pode encontrar a página do projeto [aqui](https://www.freedos.org/).
[^3]: A inicialização em modo DOS foi possível após pesquisa na documentação do FreeDOS, especialmente no arquivo "SYS.C" (que pode ser encontrado [aqui](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/dos/sys/2043/)), que indica em qual segmento o kernel espera ser carregado e quais os parâmetros são necessários. Cada sistema DOS apresenta um segmento de carregamento preferencial e esse carregamento de outras edições do DOS pode ser implementada futuramente com o auxílio dos módulos HBoot. Todo o código para o carregamento do núcleo foi desenvolvido do zero e não se baseia em algum existente.
[^4]: A iniciação em modo de compatibilidade DOS do HBoot pode ser útil para rodar ferramentas de verificação de erros no volume, desfragmentação do volume, particionador e outras ferramentas de diagnóstico, bem como de desenvolvimento, como compiladores e montadores que não são suportados pelo Hexagonix/Andromeda (as ferramentas de 16 bits, por exemplo).

### Exemplo de módulo HBoot

Abaixo é possível encontrar um exemplo de implementação de módulo HBoot:

```assembly
;;************************************************************************************
;;
;;    
;;                                Módulo do HBoot
;;        
;;                             Hexagon® Boot - HBoot
;;           
;;                 Copyright © 2020-2021 Felipe Miguel Nery Lunkes
;;                         Todos os direitos reservados
;;                                  
;;************************************************************************************

use16					

;; O módulo deve apresentar um cabeçalho especial de imagem HBoot
;; São 6 bytes, com assinatura (número mágico) e arquitetura alvo

cabecalhoHBoot:

.assinatura:  db "HBOOT"     ;; Assinatura, 5 bytes
.arquitetura: db 01h         ;; Arquitetura (i386), 1 byte

;; Configurar pilha e ponteiro

    cli				   ;; Desativar interrupções
    
    mov ax, 0x2000                 ;; Definir aqui os registradores de pilha
    mov ss, ax
    mov sp, 0
    
    sti				   ;; Habilitar interrupções
     
    clc 

    mov ax, 0x2000                 ;; Definir aqui os registradores de segmento
    mov ds, ax
    mov es, ax
    
    sti                            ;; Habilitar as interrupções

;; Seu código aqui

```

### Sistemas de arquivos suportados

* FAT16B
* FAT12 (em desenvolvimento)

Novos sistemas de arquivos serão implementados no futuro.

### Reportar bugs

O HBoot ganhou muita complexidade desde o início de seu desenvolvimento, em 2020. Devido a esse aumento de código e a natureza de sua operação (16-bit), bugs podem ser encontrados. Os mesmos podem ser reportados no repositório ou por email, disponível no final deste arquivo.

## Kernel Hexagon

### O que é

O Hexagon é um núcleo (kernel) monolítico executado em modo protegido 32-bit, desenvolvido tendo como alvo a arquitetura PC (x86). É um kernel escrito do zero, visando a velocidade e a compatibilidade de harware moderno mas também sendo capaz de ser executado em hardware mais antigo. No momento, garante um ambiente monoutilizador, apesar do uso de terminais virtuais, e monotarefa, apesar da capacidade de carregar, manter em memória e controlar mais de um processo, em uma pilha de execução de ordem cronológica. Futuramente o kernel poderá receber suporte a execução de múltiplos processos em multitarefa preemptiva. O Hexagon é um kernel Unix-like e compõe a base do Sistema Operacional Hexagonix/Andromeda, embora independente deste. Ele executa imagens executáveis no formato HAPP, desenvolvido para o Hexagon. Implementa uma API bastante sofisticada acessível através de uma chamada de sistema.

### História

O kernel foi inicialmente desenhado e escrito visando uma estrutura e funcionamento próximos de sistemas DOS (Disk Operating System), como MS-DOS, nos ano de 2015 a 2017. Sendo assim, muitas chamadas de sistema e nomes de dispositivo seguiam uma sintaxe e nomes DOS. Com o passar do tempo, houve o interesse de aproximar o então núcleo do Andromeda, que a essa altura não possuia nome e era mantido junto ao código da distribuição, a uma estrutura e funcionamento mais próximos de sistemas do tipo Unix, como BSD ou Linux, por exemplo. Desta forma, muitas partes do kernel foram reimplementadas tendo em mente o novo objetivo. O código do núcleo foi separado do restante do Sistema e se tornou independente, em questão de desenvolvimento e também de funcionamento, além de ganhar um nome, Hexagon. Foi escrita uma camada de abstração de hardware com a inclusão de chamadas de sistema conhecidas no mundo Unix, como abrir(), fechar(), ler() e escrever(). Os dispositivos ganharam nome e as unidades de disco mudaram da nomenclatura DOS e foram para nomes de dispositivo Unix. O kernel então passa a seguir um processo de inicialização conhecido, com a execução, com PID 1, do primeiro processo do usuário, init, que então carrega o restante dos componentes. Foram então escritos utilitários Unix-like que passassem a utilizar a API Unix-like do kernel, e várias ferramentas Unix-like já foram escritas desde então (2017 em diante).

### O formato executável HAPP

O formato de imagem executável HAPP foi desenvolvida para o Hexagon para permitir o desenvolvimento de imagens que possam ser verificadas e validadas quanto a arquitetura e versões mínimas do kernel necessárias para a correta execução. O cabeçalho também armazena informações importantes, permitindo ao desenvolvedor adicionar diretamente um ponto de entrada, independente de onde ele esteja no interior da imagem, algo que deveria ser redirecionado anteriormente, quando a imagem executável era no formato binário puro. A imagem HAPP também permite validar se a imagem a ser carregada é realmente uma imagem executável, impedindo então que arquivos não suportados sejam executados, mesmo que não se tratem sequer de arquivos executáveis. Também permite que o sistema verifique as dependências do código, como a já citada arquitetura, bem como os números de versão do Hexagon, que devem ser iguais ou superiores ao mínimo especificado pelo cabeçalho. Todas as imagens HAPP devem apresentar este cabeçalho completo, incluindo as sessões reservadas, a fim de funcionarem corretamente em versões posteriores do Sistema. As imagens HAPP são sempre 32-bit.

Em linguagem Assembly, a linguagem de desenvolvimento do sistema, o cabeçalho, em sua especificação 2.0:

```assembly
cabecalhoAPP:

.assinatura:      db "HAPP" ;; Assinatura
.arquitetura:     db 01h    ;; Arquitetura (i386 = 01h)
.versaoMinima:    db 8      ;; Versão mínima do Hexagon
.subversaoMinima: db 40     ;; Subversão mínima do Hexagon
.pontoEntrada:    dd        ;; Offset do ponto de entrada (referência à função principal aqui)
.tipoImagem:      db 01h    ;; Tipo de imagem executável (executável = 01h)
.reservado0:      dd 0      ;; Reservado (Dword)
.reservado1:      db 0      ;; Reservado (Byte)
.reservado2:      db 0      ;; Reservado (Byte)
.reservado3:      db 0      ;; Reservado (Byte)
.reservado4:      dd 0      ;; Reservado (Dword)
.reservado5:      dd 0      ;; Reservado (Dword)
.reservado6:      dd 0      ;; Reservado (Dword)
.reservado7:      db 0      ;; Reservado (Byte)
.reservado8:      dw 0      ;; Reservado (Word)
.reservado9:      dw 0      ;; Reservado (Word)
.reservado10:     dw 0      ;; Reservado (Word)
```

Abaixo, uma implementação de um pequeno aplicativo escrito como exemplo, que utiliza o cabeçalho e chamadas de sistema do Hexagon, escrito em linguagem Assembly x86 em sintaxe Intel e montada com o auxílio do flat assembler (FASM). Este aplicativo envia uma mensagem ao terminal e se encerra em seguida.

```assembly
;; Este é um template para a construção de um app de modo texto para 
;; o Hexagonix/Andromeda!
;;
;; Escrito por Felipe Miguel Nery Lunkes em 04/12/2020
;;
;; Voce pode gerar uma imagem HAPP executável utilizando o montador
;; FASM. Para isso, utilize a linha de comando abaixo:
;;
;; fasmX tapp.asm
;;       ou
;; fasmX tapp.asm tapp.app

use32

cabecalhoAPP:

.assinatura:      db "HAPP"    ;; Assinatura
.arquitetura:     db 01h       ;; Arquitetura (i386 = 01h)
.versaoMinima:    db 8         ;; Versão mínima do Hexagon
.subversaoMinima: db 40        ;; Subversão mínima do Hexagon
.pontoEntrada:    dd inicioAPP ;; Offset do ponto de entrada
.tipoImagem:      db 01h       ;; Imagem executável
.reservado0:      dd 0         ;; Reservado (Dword)
.reservado1:      db 0         ;; Reservado (Byte)
.reservado2:      db 0         ;; Reservado (Byte)
.reservado3:      db 0         ;; Reservado (Byte)
.reservado4:      dd 0         ;; Reservado (Dword)
.reservado5:      dd 0         ;; Reservado (Dword)
.reservado6:      dd 0         ;; Reservado (Dword)
.reservado7:      db 0         ;; Reservado (Byte)
.reservado8:      dw 0         ;; Reservado (Word)
.reservado9:      dw 0         ;; Reservado (Word)
.reservado10:     dw 0         ;; Reservado (Word)

;;*************************************************************

include "andrmda.s" ;; Incluir as chamadas de sistema

;;*************************************************************

;; Variaveis e constantes

msg: db 10, 10, "Este e um template com um exemplo de aplicativo HAPP simples!", 10, 0

;;*************************************************************

;; Ponto de entrada

inicioAPP:

    mov esi, msg

    imprimirString ;; Aqui temos um macro que configura e chama uma função da API

    Andromeda encerrarProcesso ;; Outro macro que solicita qual chamada realizar
``` 

Uma documentação mais detalhada do Hexagon será disponibilizada no futuro.

## Ambiente Hexagonix:

O Hexagonix implementa, junto ao Hexagon, uma série de utilitários Unix-like, com funcionalidade e sintaxe de uso semelhante à sistemas UNIX e Unix-like. **Utilitários como init, login, sh, top, ps, cp, rm, cat, clear, man, dentre outros, estão inclusos na distribuição padrão do Hexagonix**. Estes utilitários compõem o pacote de utilitários base do Hexagonix. As ferramentas de inicialização de ambiente de modo usuário e login estão neste pacote, bem como vários arquivos de configuração deste ambiente. Estes utilitários não apresentam, no geral, uma interface gráfica, apenas uma interface em linha de comando (CLI). Entretanto, podem ser solicitados por aplicativos que apresentem interface gráfica. Este ambiente está disponível tanto na distribuição do [Hexagonix](hexagonix.img) quanto na distribuição [Andromeda](andromeda.img).

### Alguns aplicativos e utilitários do ambiente Hexagonix

O Hexagonix inclui muitos dos utilitários Unix que você pode já estar familiarizado, como por exemplo:

* init
* login
* ls
* cat
* cp
* rm
* clear
* top
* ps
* man
* su
* sh (shell padrão)
* uname
* whoami, entre outros.

### Aplicativos de terceiros disponíveis para o Hexagonix

* [Flat Assembler (fasm)](https://flatassembler.net/index.php)

O Hexagonix recebeu um port do montador [Fasm](https://flatassembler.net/index.php), que foi adaptado para o Hexagonix, permitindo ao usuário desenvolver aplicativos diretamente no sistema. As alterações adicionadas ao código, assim como licença do software, podem ser encontradas no [repositório do fasm para o Hexagonix](https://github.com/hexagonix/fasm). Este repositório é um fork do [repositório original](https://github.com/tgrysztar/fasm). O código adicionado é baseado em modificações realizadas do código original e adições autorais. Esse código modificado/autoral pode ser encontrado no repositório, [clicando aqui](https://github.com/hexagonix/fasm/tree/master/SOURCE/HEXAGONIX).
 
## Ambiente Andromeda:

O ambiente Andromeda é construído sobre a base sólida fornecida pelo Hexagonix, incluindo aplicativos e utilitários que não implementam a filosofia Unix ou apresentam sintaxe e forma de uso bastante diferentes do que se esperaria de um ambiente Unix. Desta forma, eles são separados como **aplicativos Andromeda**, e não fazem parte da distribuição padrão do Hexagonix. Aqui estão o aplicativo de configurações do Sistema, calculadora, gerenciador de fontes, editores de texto e a IDE desenvolvida para o Andromeda. Estes utilitários podem ou não apresentar uma interface gráfica. Juntamente a eles, compõem o ambiente Andromeda bibliotecas desenvolvidas para permitir o desenvolvimento de aplicativos, como a biblioteca **Estelar**. Esse ambiente só está disponível na distribuição [Andromeda](andromeda.img).

### Alguns aplicativos e utilitários do ambiente Andromeda

* Configurações do Sistema (Config)
* Editor de texto Quartzo
* IDE Lyoko para desenvolvimento de aplicativos
* Piano eletrônico return Piano;
* Utilitário de comunicação serial
* Andromeda Shell (ASH) - Um novo shell para o Andromeda
* Calculadora do Andromeda
* Utilitário de alteração de fonte
* Utilitário de desligamento do Andromeda

### Aplicativos de terceiros disponíveis para o Andromeda

Ainda não existem aplicativos de terceiros disponíveis para o ambiente Andromeda. Caso esteja interessado, você pode construir o primeiro!

## Fontes do Hexagonix:

A instalação padrão do Hexagonix também fornece uma série de fontes que podem ser carregadas pelo aplicativo de configurações ou utilitário de fontes (gerenciador de fontes). Esses arquivos são utilizados para alterar a fonte de exibição em modo gráfico do Hexagonix e Andromeda.

# Bibliotecas de desenvolvimento do sistema:

O Hexagonix/Andromeda também fornece funções que devem ser utilizadas para interagir com o próprio ambiente do sistema. As bibliotecas são utilizadas para acessar funções implementadas pelo Hexagon ou pelas próprias bibliotecas, permitindo o desenvolvimento facilitado de aplicativos e utilitários tanto para o ambiente Hexagonix quanto para o Andromeda. As bibliotecas implementam funções para exibição de texto, cálculos matemáticos, envio de mensagens, abertura de arquivos e dispositivos e muito mais. A biblioteca básica (andrmda.s ou hexagonix.s) fornecem funções acessíveis para ambos os ambientes possíveis de distribuição, enquanto outras bibliotecas podem ser exclusivas do ambiente Andromeda. Essas bibliotecas incluem funções gráficas para montar interfaces em modo gráfico (Andromeda), bem como funções para verificar a versão do sistema atualmente em execução (Hexagonix e Andromeda). Os utilitários base Hexagonix realizam a checagem da versão do Hexagon para verificar se podem ser executados, utilizando o utilitário Unix uname ou diretamente por uma chamada de sistema do Hexagon.

# Um pouco sobre a inicialização do sistema:

Após a inicialização do firmware, o [BIOS]](https://pt.wikipedia.org/wiki/BIOS) ou outro firmware, como [UEFI]](https://pt.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) em modo legado, realiza a busca de um volume/disco marcado como inicializável e, ao encontrar, carrega o primeiro setor para o endereço 0x7C00. No caso de um volume Hexagon, no primeiro setor do volume está localizado o componente denominado Saturno. Saturno é o gerenciador de inicialização MBR de um volume Hexagon e atua como primeiro estágio na cadeia de carregamento do Sistema. Ele realiza a procura, no volume, do segundo estágio, bem mais robusto, o Hexagon Boot (HBoot). O HBoot não apresenta as mesmas limitações do componente anterior, uma vez que não está restrito ao tamanho de 512-bytes. Ao iniciar, o HBoot realiza uma série de testes e diagnósticos da máquina, verificando quais discos/volumes estão disponíveis na máquina, qual a quantidade de memória RAM instalada e inicializando alguns periféricos, como portas seriais, além de verificar o processador instalado quanto a sua capacidade de executar o Hexagon. Caso a quantidade de memória RAM instalada seja menor que o mínimo, o processador não seja suportado ou ocorra algum erro em algum periférico essencial, a protocolo de inicialização é cancelado. Caso os testes sejam bem sucedidos, ocorre a procura, no volume, do arquivo que contêm o kernel Hexagon, com seu carragamento, construção de uma estrutura de parâmetros, configuração de registradores com informações básicas de hardware e posterior execução. O HBoot também é capaz de carregar e executar módulos no formato HBoot, bem como iniciar um sistema do tipo DOS cujos arquivos estejam presentes no volume Hexagon (até o momento, apenas o FreeDOS é suportado). Também é capaz de realizar alguns testes de hardware sob demanda, como som e gráficos. Após o carregamento do Hexagon, o kernel recebe o controle do dispositivo e realiza a configuração dos periféricos, constrói estruturas internas de controle e inicia o primeiro processo de usuário, com PID 1, normalmente o Inicializador do Sistema, ou init. O init irá ler o arquivo de configuração "INIT.UNX" no volume e iniciar os serviços lá descritos, geralmente o Gerenciador de Login e Usuários, ou simplemente login. Este, por sua vez, busca as informações em "USUARIO.UNX" e as compara com as entradas do usuário, e, caso as credenciais sejam válidas, inicia o primeiro shell ou utilitário descrito na entrada de usuário. Após, o Hexagon entra em modo administrativo e gerencia requisições dos aplicativos e periféricos, expondo a API para construção e execução dos demais componentes do Sistema (para mais informações, consulte o arquivo de cabeçalho "ANDRMDA.S", que já documenta a API).

# Como testar o Hexagonix ou o Andromeda:

## Requisitos do sistema

### Requisitos mínimos

* Processador: Pentium III (1999) com suporte a SSE e MMX ou mais recente;
* Memória RAM: 32 Mb mínimo (uma instalação mínima com 32 Mb costuma ser suficiente, na maioria dos casos);
* Disco rígido: disco rígido IDE ou SATA com mínimo de 50 Mb;
* Periféricos necessários:
  - Porta serial (1-4);
  - Porta paralela (1-4);
  - Teclado PS/2 ou USB;
  - Placa de vídeo VGA com 2 Mb de memória de vídeo (com suporte a cores).

### Recomendado

* Processador: Pentium D ou mais recente;
* Memória RAM: 50 Mb;
* Periféricos opcionais:
  - Mouse PS/2 ou USB;
  - Placa de vídeo com > 2 Mb de memória de vídeo.

## Obter as imagens de disco com a instação do sistema 

Para testar o Hexagonix ou Andromeda, você vai precisar de uma das imagens de disco disponíveis neste repositório, bem como a ferramenta [qemu](https://www.qemu.org) instalada em seu computador. A imagem também pode ser utilizada para a gravação em um disco físico em uma máquina real. 

Para testar o Hexagonix, obtenha o arquivo ['hexagonix.img'](hexagonix.img) neste repositório.
Para testar o Andromeda, obtenha o arquivo ['andromeda.img'](andromeda.img) neste repositório.

## Para o teste em ambiente virtualizado

Você deve fornecer ao menos 32 MB de RAM para a máquina virtual. Normalmente, a linha de comando abaixo cumpre todos os requisitos para a execução do sistema:

```
qemu-system-i386 -hda andromeda.img -m 32 -soundhw pcspk
qemu-system-i386 -hda hexagonix.img -m 32 -soundhw pcspk
```

Lembrando que você deve utilizar uma versão/edição do qemu que consiga executar software escrito para a arquitetura x86. Para realizar o download e instalação do qemu, clique [aqui](https://www.qemu.org/download/).

## Para teste em máquina física

Você deve utilizar o Linux/macOS ou alguma ferramenta Windows que te permita gravar essa imagem em disco.

No Linux/macOS/Unix, use a linha abaixo:

```
dd if=andromeda.img of=/dev/unidade
```
onde unidade equivale ao dispositivo desejado. Reinicie seu computador e teste o sistema. Vale lembrar que o modo de boot seguro não é suportado, além de que o boot só é suportado em BIOS ou no modo legado BIOS do UEFI.

# Capturas de tela do sistema

## Andromeda

![Andromeda 1](Img/Andromeda1.png)
![Andromeda 2](Img/Andromeda2.png)
![Andromeda 3](Img/Andromeda3.png)
![Andromeda 4](Img/Andromeda4.png)
![Andromeda 5](Img/Andromeda5.png)

Você pode ver mais [aqui](https://github.com/hexagonix/Distro/tree/main/Img).

## Hexagonix

![Hexagonix 1](Img/Hexagonix1.png)
![Hexagonix 2](Img/Hexagonix2.png)
![Hexagonix 3](Img/Hexagonix3.png)
![Hexagonix 4](Img/Hexagonix4.png)
![Hexagonix 5](Img/Hexagonix5.png)

Você pode ver mais [aqui](https://github.com/hexagonix/Distro/tree/main/Img).

# Idiomas

Neste momento, tanto o sistema quanto a documentação estão disponíveis apenas em português. O documentação em inglês estará disponível em breve, e há planos para suporte ao inglês como possibilidade de idioma principal, além do português (grande parte do trabalho já foi feita).

# Autor & contato

* [Felipe Miguel Nery Lunkes](https://github.com/felipenlunkes)

Sinta-se a vontade de me contatar, reportar bugs ou se interessar em participar do projeto.

## E-mail:

* hexagonixdev@gmail.com (PT/EN) 
* felipemiguel_nery@hotmail.com (PT/EN)

## Redes sociais:

* [Twitter](https://twitter.com/redLipes)

Versão deste arquivo: 3.5

<!-- Versão em inglês -->

# Hexagonix/Andromeda Operating System

Welcome to the Hexagonix/Andromeda Operating System

## Copyright Notes

Hexagonix/Andromeda was developed from scratch by [Felipe Lunkes](https://github.com/felipenlunkes).

Read the [license](LICENSE) for more information on copyright, code ownership and redistribution.

* Andromeda Operating System. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. All rights reserved.
* Hexagon kernel. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. All rights reserved.
* Saturn Boot Manager. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. All rights reserved.
* Hexagon Boot (HBoot). Copyright © 2020-2022 Felipe Miguel Nery Lunkes. All rights reserved.

## First of all

At the end of this file you will find a tutorial to run Hexagonix/Andromeda on your computer, both in a virtualized version and natively. Remember that you must have a computer with x86 architecture or an emulator if you are using a device of another architecture for testing.

* [System Documentation (under construction)](https://github.com/hexagonix/Distro/tree/main/Doc)

# About the system

## Development

Hexagonix/Andromeda and all its components have been in development since 2015 and were written completely in Assembly language.

## Why two names? Hexagonix and Andromeda, what are they?

In the beginning, Andromeda was intended to be a complete operating system, consisting of the kernel, libraries, graphical and text interface and utilities. Later, with the passage of time and the change in approach to the system's architecture and objectives, the components were separated and became independent projects in terms of functioning, organization and development. As you can see below, the core of Andromeda was separated from the rest of the Andromeda code tree, becoming an independent project, even given a name, Hexagon. From then on, the idea of ​​making the composition of the system more flexible and allowing the development of distributions, as in GNU/Linux, arose. In this way, Hexagon distributions could be created, grouping the components necessary for the basic operation (Hexagonix) and allowing the extension of the system if necessary, with new components, modules and utilities, with the userland defined in each case. With the architecture change of the system itself, with the core approaching a Unix-like architecture, new utilities in Unix style and syntax were developed and kept separate, in another project. From the original Andromeda project we have Andromeda-specific graphical libraries and applications. A base system was then created, which by itself can be fully implemented, and became the base of Andromeda. This base system is called Hexagonix, and is composed of the HBoot boot loader, the Hexagon kernel, the shell, Unix environment libraries (here called Hexagonix environment) and Unix utilities. This system is fully functional, but lacks graphical resources and applications developed for the Andromeda environment. In this way, Andromeda stands out for being an extra layer built on the base of Hexagonix, with graphics resources, a graphics library and utilities that work on top of Hexagonix and extend its function. This built environment was named the Andromeda environment. To meet different needs, the two distributions will always be maintained. Both versions are functional and can be used depending on the desired end use. In summary, both Hexagonix and Andromeda are Hexagon kernel distributions, differing in the components included.

To better understand this distribution model, a suitable example would be what happens with macOS (Apple)[^5]. macOS is a Unix-like operating system built on top of Darwin, a free operating system composed of the XNU kernel, libraries and utilities, adding the Aqua GUI and other applications and utilities developed by Apple and other vendors on top of Darwin. The Darwin environment is easily accessed and observed through macOS, such as using the terminal, for example. Darwin is a complete and functional system, but it lacks some graphical features, for example, which are only distributed together with macOS. In this analogy, we have macOS as Andromeda and Darwin as Hexagonix.

[^5]: You can get more information about the relationship between Darwin and macOS [here](https://en.wikipedia.org/wiki/Darwin_(operating_system)).

## And the source code?

The project's source code is not yet publicly available, but there are plans to make it available in the future. However, distribution of disk images with both Hexagonix and Andromeda is free. Please note the [license](LICENSE) available in this repository for more information.

## What is an operational system?

The Hexagonix/Andromeda Operating System is a collection of software pieces that manage the hardware of the computer where it is installed, allowing the loading and operation of applications and communication between the different devices connected to the device. It is composed of several components, which act in the computer boot process, resource testing and loading of the operating system kernel (core), the kernel, a user interaction interface and a series of utilities.
Both hexagonix and Andromeda are distributions that incorporate a Unix-like kernel, called Hexagon, support libraries, utilities developed exclusively for the Andromeda environment, and Unix-like command-line utilities (the latter and the Hexagon kernel itself are already there configure a base operating system, Hexagonix).

## The Hexagonix/Andromeda history:

Andromeda started as a structured implementation similar to DOS-like systems, with an interpreter with built-in commands with names, syntaxes and results similar to a generic DOS. The command interpreter had file manipulation and other commands internally, as in conventional DOS systems. Disk drives were also defined as letters. Later, there was a growing interest and fascination in the functioning of Unix systems and all the code was rewritten or adapted to make the System kernel a Unix-like kernel. All System components, just like in DOS, were kept in a single tree until then. With version 1.5 of Andromeda, codenamed "Unix-like", the kernel has been heavily modified and rewritten to suit the Unix philosophy. Changes even included the way devices were handled, with writing a hardware abstraction layer with managing devices as files, as well as adding system calls open(), close(), write() and read(). The base Unix utilities were also written, with the removal of commands from the standard interpreter, which was rewritten to make way for a Unix-like shell. The internal commands were moved to the utilities, which now have a Unix-style structure and syntax. The rest of the utilities, such as mount, were written, already taking advantage of the open() call, which is also used to mount volume, in addition to opening ordinary files on the volume. The open() call is also used to start other peripherals such as serial and parallel ports. The write() call also works with devices and files as well as close(). A VFS (Virtual File System) was also introduced, which in the future will support various file systems and makes file management transparent to the System, programmers and users. Also included are new hardware management functions and many improvements and bug fixes. The System gains new Unix utilities to date. After this change in proposal and architecture, the components were separated and allocated to specific projects. The union of these components forms the operating system. In the case of Hexagonix, we have HBoot, Hexagon, shell, Unix libraries and applications, while Andromeda extends Hexagonix, incorporating other libraries and applications that use them.

## Hexagonix/Andromeda versioning:

The operating system features version numbering independent of the associated components. Each component, from the boot loader to a simple utility, is given an independent version number that reflects its development status. A Hexagonix/Andromeda version number has three sets of numbers divided into three blocks separated by a period character ".". The first one represents the major version number and is based on number one. The second number refers to the release, this is the number that varies from one Hexagonix/Andromeda release to another and distinguishes between the major versions of the System, in addition to being used as a version number that is checked by applications and utilities to verify whether the system version meets the minimum requirements for running the software. The third is the revision number of each major release and, if it is 0, it can be omitted, leaving the version with only two digit blocks. An example would be versions "1.14.4", whose base version is always 1, so far, 14 indicates the release (this refers, most of the time, to the actual version of the System. Think, for example, of the system of numbering Apple with Mac OS X/OS X/macOS up to version 11.0 Big Sur, which always starts with 10 and is followed by the release and revision number). Number 4, on the other hand, would be the revision within the major release, which concerns fixing bugs and adding some functionality that does not profoundly change the System or its use.

Normally, Hexagonix and Andromeda have the same major version numbering, but this is not necessarily mandatory. Version numbers may differ at some point, as well as the components of each distribution. The Hexagon version, for example, can be different even with identical version numbers, but this kind of divergence will always be avoided.

# System components

## Saturn

The first component of Hexagonix/Andromeda is Saturn. It is responsible for taking control of the boot process performed by the BIOS/UEFI and searching the volume for the second boot stage. For that, it implements a driver for reading a FAT16 file system. The second boot stage (see below) can implement drivers for other file systems and is responsible for finding Hexagon, loading HBoot modules or loading a DOS compatible system (BETA).

## Hexagon Boot (HBoot)

Hexagon Boot (HBoot) is a component designed to allow booting of the Hexagon kernel. Until then, initialization was performed by just one stage, which defined a very basic environment, loaded the Hexagon into memory, and immediately passed control to it, providing a very small and limited set of parameters, since the code for that stage stays restricted to 512 bytes, which limits the performance of several tests and data processing. With HBoot, it was possible to expand the number of tasks performed before the Hexagon runs, as well as the possibility to provide more information regarding the machine and boot environment. This is particularly important to allow the creation of a device tree that Hexagon can use to decide how to handle each identified device. HBoot is able to check which disk drives are available on the machine, emit a boot tone, obtain the amount of available RAM memory installed and allow or disallow the boot process to proceed according to this information. If no user interaction is detected 3 seconds after all essential tests and activities to create a boot environment for Hexagon, the system will load and run Hexagon (present in a file in the volume named **HEXAGON.SIS**** ) being unloaded from memory. The interaction with HBoot is done by pressing the F8 key after the respective message appears on the screen.

### Other functions

* HBoot allows loading modules in HBoot format, which may be useful in the future to allow for hardware tests such as memory and disk tests if the modules are available on disk. Modules can also be used to extend HBoot's functions. The format specification is now available and an example can be found below. These modules can be used to test specific devices, obtain hardware information, or load files into file systems not originally supported by HBoot.
* In the context of Hexagonix development, HBoot can also load directly, from a currently built-in module (this function will be moved to a standalone module as soon as possible) the core of the FreeDOS open source operating system[^6] , so that established and robust utility tools that run in a DOS environment can run on the Hexagonix/Andromeda volume and files. FreeDOS was chosen because of its feature of a kernel composed of a single file, usually "KERNEL.SYS"[^7], in addition to its free and free distribution. On the other hand, other DOS, such as MS-DOS, prior to version 7.0, use two files that must be contiguous on the disk, and this is not possible here, since the installation of FreeDOS already takes place on a Hexagonix volume, with the kernel copy , command interpreter and other DOS utilities, the main operating system being Hexagonix/Andromeda, with optional launching of FreeDOS for some special activity[^8]. If the FreeDOS system components are not present on the disk (the copy of FreeDOS files is not part of the default image), booting into DOS compatibility mode will not occur.

[^6]: You can find the project page [here](https://www.freedos.org/).
[^7]: Booting in DOS mode was possible after searching the FreeDOS documentation, especially the "SYS.C" file (which can be found [here](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/dos/sys/2043/), which indicates in which segment the kernel expects to be loaded and which parameters are needed. Each DOS system has a preferred loading segment and this loading of other DOS editions can be implemented in the future with the help of HBoot modules. All code for core loading was developed from scratch and is not based on any existing ones.
[^8]: Booting in DOS compatibility mode of HBoot can be useful for running volume error checking, volume defragmenting, partitioner and other diagnostic tools, as well as development tools such as non-compilers and assemblers. supported by Hexagonix/Andromeda (the 16-bit tools, for example).

### HBoot Module Example

Below you can find an example of HBoot module implementation:

```assembly
;;**************************************************** ***********************************
;;
;;
;; HBoot Module
;;
;; Hexagon® Boot - HBoot
;;
;; Copyright © 2020-2021 Felipe Miguel Nery Lunkes
;; All rights reserved
;;
;;**************************************************** ***********************************

use16

;; The module must have a special HBoot image header
;; There are 6 bytes, with signature (magic number) and target architecture

HBootHeader:

.signature:    db "HBOOT" ;; Signature, 5 bytes
.architecture: db 01h     ;; Architecture (i386), 1 byte

;; Configure stack and pointer

    cli;; Disable interrupts
    
    mov ax, 0x2000 ;; Define stack registers here
    mov ss, ax
    mov sp, 0
    
    sti;; Enable interrupts
     
    clc

    mov ax, 0x2000 ;; Define segment registers here
    mov ds, ax
    mov es, ax
    
    sti;; Enable interrupts

;; Your code here

```

### Supported file systems

* FAT16B
* FAT12 (under development)

New file systems will be implemented in the future.

### Report bugs

HBoot has gained a lot of complexity since the beginning of its development in 2020. Due to this increase in code and the nature of its operation (16-bit), bugs can be found. They can be reported in the repository or by email, available at the end of this file.

## Kernel Hexagon

### What is it

Hexagon is a monolithic kernel (kernel) running in 32-bit protected mode, developed with the PC architecture (x86) in mind. It is a kernel written from scratch, aiming for the speed and compatibility of modern hardware but also being able to run on older hardware. For the moment, it guarantees a single-user environment, despite the use of virtual terminals, and monotasking, despite the ability to load, keep in memory and control more than one process, in a chronologically-ordered execution stack. In the future, the kernel will be able to support the execution of multiple processes in preemptive multitasking. Hexagon is a Unix-like kernel and forms the basis of the Hexagonix/Andromeda Operating System, although independent of it. It runs executable images in HAPP format, developed for Hexagon. It implements a very sophisticated API accessible via a system call.

### History

The kernel was initially designed and written aiming at a structure and functioning similar to DOS (Disk Operating System) systems, such as MS-DOS, in the year 2015 to 2017. Therefore, many system calls and device names followed a syntax and names FROM. Over time, there was an interest in bringing the then core of Andromeda, which at that time did not have a name and was kept with the distribution code, to a structure and operation closer to Unix-like systems, such as BSD or Linux , for example. In this way, many parts of the kernel were redeployed with the new goal in mind. The core code was separated from the rest of the System and became independent, in terms of development as well as functioning, in addition to gaining a name, Hexagon. A hardware abstraction layer was written with the inclusion of system calls known in the Unix world, such as open(), close(), read() and write(). Devices were named and disk drives were changed from DOS naming to Unix device names. The kernel then goes through a known boot process, with the execution, with PID 1, of the user's first process, init, which then loads the rest of the components. Unix-like utilities were then written that used the kernel's Unix-like API, and several Unix-like tools have been written since then (2017 onwards).

### The HAPP executable format

The HAPP executable image format was developed for Hexagon to allow the development of images that can be verified and validated for architecture and minimum kernel versions necessary for correct execution. The header also stores important information, allowing the developer to directly add an entry point, regardless of where it is inside the image, something that would have been redirected earlier when the executable image was in pure binary format. The HAPP image also allows you to validate that the image to be loaded is really an executable image, thus preventing unsupported files from being executed, even if they are not even executable files. It also allows the system to check code dependencies, such as the aforementioned architecture, as well as Hexagon version numbers, which must be equal to or greater than the minimum specified by the header. All HAPP images must have this complete header, including reserved sessions, in order to function correctly in later versions of the System. HAPP images are always 32-bit.

In assembly language, the system development language, the header, in its 2.0 specification:

```assembly
APPHeader:

.signature:          db "HAPP" ;; Signature
.architecture:       db 01h ;; Architecture (i386 = 01h)
.Minimum Version:    db 8 ;; Minimal version of Hexagon
.Minimum subversion: db 40 ;; Minimal Hexagon Subversion
.entrypoint:         dd ;; Input point offset (reference to main function here)
.ImageType:          db 01h ;; Executable image type (executable = 01h)
.reserved0:          dd 0 ;; Reserved (Dword)
.reserved1:          db 0 ;; Reserved (Byte)
.reserved2:          db 0 ;; Reserved (Byte)
.reserved3:          db 0 ;; Reserved (Byte)
.reserved4:          dd 0 ;; Reserved (Dword)
.reserved5:          dd 0 ;; Reserved (Dword)
.reserved6:          dd 0 ;; Reserved (Dword)
.reserved7:          db 0 ;; Reserved (Byte)
.reserved8:          dw 0 ;; Reserved (Word)
.reserved9:          dw 0 ;; Reserved (Word)
.reserved10:         dw 0 ;; Reserved (Word)
```

Below is an implementation of a small application written as an example, which uses the Hexagon header and system calls, written in x86 assembly language in Intel syntax and assembled with the aid of a flat assembler (FASM). This app sends a message to the terminal and then exits.

```assembly
;; This is a template for building a text mode app for
;; the Hexagonix/Andromeda!
;;
;; Written by Felipe Miguel Nery Lunkes on 12/04/2020
;;
;; You can generate an executable HAPP image using the assembler
;; FASM. To do this, use the command line below:
;;
;; fasmX tapp.asm
;; or
;; fasmX tapp.asm tapp.app

use32

APPHeader:

.signature:          db "HAPP" ;; Signature
.architecture:       db 01h ;; Architecture (i386 = 01h)
.Minimum Version:    db 8 ;; Minimal version of Hexagon
.Minimum subversion: db 40 ;; Minimal Hexagon Subversion
.Entrypoint:         dd startAPP ;; Input point offset
.ImageType:          db 01h ;; executable image
.reserved0:          dd 0 ;; Reserved (Dword)
.reserved1:          db 0 ;; Reserved (Byte)
.reserved2:          db 0 ;; Reserved (Byte)
.reserved3:          db 0 ;; Reserved (Byte)
.reserved4:          dd 0 ;; Reserved (Dword)
.reserved5:          dd 0 ;; Reserved (Dword)
.reserved6:          dd 0 ;; Reserved (Dword)
.reserved7:          db 0 ;; Reserved (Byte)
.reserved8:          dw 0 ;; Reserved (Word)
.reserved9:          dw 0 ;; Reserved (Word)
.reserved10:         dw 0 ;; Reserved (Word)

;;**************************************************** *************

include "andrmda.s" ;; Include system calls

;;**************************************************** *************

;; Variables and constants

msg: db 10, 10, "This is a template with a simple HAPP application example!", 10, 0

;;**************************************************** *************

;; entry point

startAPP:

    mov esi, msg

    printString ;; Here we have a macro that configures and calls an API function.

    Andromeda terminateProcess ;; Another macro that asks which call to make
```

More detailed Hexagon documentation will be made available in the future.

## Hexagonix environment:

Hexagonix implements, together with Hexagon, a series of Unix-like utilities, with functionality and syntax similar to UNIX and Unix-like systems. **Utilities such as init, login, sh, top, ps, cp, rm, cat, clear, man, and more are included in the standard Hexagonix distribution**. These utilities make up the base Hexagonix utility package. The login and user mode environment startup tools are in this package, as well as several configuration files for this environment. These utilities generally don't have a graphical interface, just a command line interface (CLI). However, they can be requested by applications that have a graphical interface. This environment is available in both the [Hexagonix](hexagonix.img) distribution and the [Andromeda](andromeda.img) distribution.

### Some applications and utilities in the Hexagonix environment

Hexagonix includes many of the Unix utilities that you may already be familiar with, for example:

* init
* Login
* ls
* cat
* cp
* rm
* clear
* top
* ps
* man
* su
* sh (default shell)
* uname
* whoami, among others.

### Third Party Applications Available for Hexagonix

* [Flat Assembler (fasm)](https://flatassembler.net/index.php)

Hexagonix received an assembler port [Fasm](https://flatassembler.net/index.php), which was adapted for Hexagonix, allowing the user to develop applications directly on the system. Changes added to the code, as well as the software license, can be found in the [fasm repository for Hexagonix](https://github.com/hexagonix/fasm). This repository is a fork of the [original repository](https://github.com/tgrysztar/fasm). Added code is based on modifications made to the original code and copyright additions. This modified/authored code can be found in the repository, [by clicking here](https://github.com/hexagonix/fasm/tree/master/SOURCE/HEXAGONIX).

## Andromeda Environment:

The Andromeda environment is built on the solid foundation provided by Hexagonix, including applications and utilities that either don't implement the Unix philosophy or have quite different syntax and usage than you'd expect from a Unix environment. As such, they are separated as **Andromeda apps**, and are not part of the standard Hexagonix distribution. Here are the System settings app, calculator, font manager, text editors and the IDE developed for Andromeda. These utilities may or may not have a graphical interface. Together with them, the Andromeda environment comprises libraries developed to allow the development of applications, such as the **Stellar** library. This environment is only available in the [Andromeda](andromeda.img) distribution.

### Some apps and utilities from the Andromeda environment

* System Settings (Config)
* Quartz text editor
* Lyoko IDE for application development
* Electronic Piano return Piano;
* Serial communication utility
* Andromeda Shell (ASH) - A new shell for Andromeda
* Andromeda Calculator
* Font change utility
* Andromeda shutdown utility

### Third-party apps available for Andromeda

There are no third-party applications available for the Andromeda environment yet. If interested, you can build the first one!

## Hexagonix fonts:

The default Hexagonix installation also provides a number of fonts that can be loaded by the settings application or font utility (font manager). These files are used to change the graphic mode display font of Hexagonix and Andromeda.

# System development libraries:

Hexagonix/Andromeda also provides functions that must be used to interact with the system environment itself. Libraries are used to access functions implemented by Hexagon or by the libraries themselves, allowing easy development of applications and utilities for both the Hexagonix and Andromeda environments. Libraries implement functions for displaying text, math calculations, sending messages, opening files and devices, and much more. The base library (andrmda.s or hexagonix.s) provides accessible functions for both possible distribution environments, while other libraries may be unique to the Andromeda environment. These libraries include graphical functions to build interfaces in graphical mode (Andromeda), as well as functions to check the version of the system currently running (Hexagonix and Andromeda). The Hexagonix base utilities perform a Hexagon version check to see if they can be run using the Unix uname utility or directly via a Hexagon system call.

# A little bit about system startup:

After booting the firmware, the [BIOS](https://en.wikipedia.org/wiki/BIOS) or other firmware, such as [UEFI](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) in legacy mode, performs fetches a volume/disk marked bootable and, when found, loads the first sector to address 0x7C00. In the case of a Hexagon volume, the component named Saturn is located in the first sector of the volume. Saturn is the MBR boot manager of a Hexagon volume and acts as the first stage in the System load chain. It performs the search, in the volume, of the second stage, much more robust, the Hexagon Boot (HBoot). HBoot does not have the same limitations as the previous component, as it is not restricted to 512-byte size. When starting, HBoot performs a series of machine tests and diagnostics, checking which disks/volumes are available on the machine, how much RAM memory is installed and initializing some peripherals, such as serial ports, in addition to checking the installed processor for its ability to run Hexagon. If the amount of RAM memory installed is less than the minimum, the processor is not supported or an error occurs in an essential peripheral, the initialization protocol is canceled. If the tests are successful, the volume is searched for the file containing the Hexagon kernel, with its loading, construction of a parameter structure, configuration of registers with basic hardware information and subsequent execution. HBoot is also capable of loading and executing modules in the HBoot format, as well as booting a DOS-like system whose files are present on the Hexagon volume (so far, only FreeDOS is supported). It is also capable of performing some hardware tests on demand, such as sound and graphics. After loading the Hexagon, the kernel takes control of the device and performs peripheral configuration, builds internal control structures and starts the first user process, with PID 1, usually the System Initiator, or init. init will read the configuration file "INIT.UNX" from the volume and start the services described there, usually the Login and User Manager, or simply login. This, in turn, fetches the information in "USER.UNX" and compares it with the user's entries, and if the credentials are valid, starts the first shell or utility described in the user's entry. Afterwards, Hexagon goes into administrative mode and manages requests from applications and peripherals, exposing the API for building and executing the other components of the System (for more information, see the header file "ANDRMDA.S", which already documents the API).

# How to test Hexagonix or Andromeda:

## System requirements

### Minimum requirements

* Processor: Pentium III (1999) with SSE and MMX support or newer;
* RAM memory: 32 Mb minimum (a minimum installation with 32 Mb is usually sufficient in most cases);
* Hard disk: IDE or SATA hard disk with a minimum of 50 Mb;
* Necessary peripherals:
  - Serial port (1-4);
  - Parallel port (1-4);
  - PS/2 or USB keyboard;
  - VGA video card with 2 Mb video memory (with color support).

### Recommended

* Processor: Pentium D or newer;
* RAM memory: 50 Mb;
* Optional peripherals:
  - PS/2 or USB mouse;
  - Video card with > 2 Mb of video memory.

## Get disk images with system installation

To test Hexagonix or Andromeda, you will need one of the disk images available in this repository, as well as the [qemu](https://www.qemu.org) tool installed on your computer. The image can also be used for writing to a physical disk on a real machine.

To test Hexagonix, get the ['hexagonix.img'](hexagonix.img) file from this repository.
To test Andromeda, get the ['andromeda.img'](andromeda.img) file from this repository.

## For testing in a virtualized environment

You must provide at least 32 MB of RAM for the virtual machine. Typically, the command line below fulfills all requirements for running the system:

```
qemu-system-i386 -hda andromeda.img -m 32 -soundhw pcspk
qemu-system-i386 -hda hexagonix.img -m 32 -soundhw pcspk
```

Remembering that you must use a qemu version/edition that can run software written for the x86 architecture. To download and install qemu, click [here](https://www.qemu.org/download/).

## For physical machine testing

You must use Linux/macOS or some Windows tool that allows you to burn this image to disk.

On Linux/macOS/Unix, use the line below:

```
dd if=andromeda.img of=/dev/unit
```
where unit equals the desired device. Restart your computer and test the system. Keep in mind that secure boot mode is not supported, and booting is only supported in BIOS or UEFI BIOS legacy mode.

# System screenshots

## andromeda

![Andromeda 1](Img/Andromeda1.png)
![Andromeda 2](Img/Andromeda2.png)
![Andromeda 3](Img/Andromeda3.png)
![Andromeda 4](Img/Andromeda4.png)
![Andromeda 5](Img/Andromeda5.png)

You can see more [here](https://github.com/hexagonix/Distro/tree/main/Img).

## Hexagonix

![Hexagonix 1](Img/Hexagonix1.png)
![Hexagonix 2](Img/Hexagonix2.png)
![Hexagonix 3](Img/Hexagonix3.png)
![Hexagonix 4](Img/Hexagonix4.png)
![Hexagonix 5](Img/Hexagonix5.png)

You can see more [here](https://github.com/hexagonix/Distro/tree/main/Img).

# Languages

At the moment, both the system and the documentation are only available in Portuguese. Documentation in English will be available soon, and there are plans to support English as a primary language possibility in addition to Portuguese (much of the work has already been done).

# Author & Contact

* [Felipe Miguel Nery Lunkes](https://github.com/felipenlunkes)

Feel free to contact me, report bugs or be interested in participating in the project.

## Email:

* hexagonixdev@gmail.com (PT/EN)
* felipemiguel_nery@hotmail.com (PT/EN)

## Social networks:

* [Twitter](https://twitter.com/redLipes)


