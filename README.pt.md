<!--

Versão deste arquivo: 5.0

Copyright © 2021-2022 Felipe Miguel Nery Lunkes
Todos os direitos reservados.

-->

# Sistema Operacional Hexagonix/Andromeda

# Antes de mais nada - um breve atalho para ir direto ao ponto


<details title="Licença" align='left'>
<br>
<summary align='left'><strong>Licença</strong></summary>

Hexagonix Operating System

BSD 3-Clause License

Copyright (c) 2015-2022, Felipe Miguel Nery Lunkes
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its
   contributors may be used to endorse or promote products derived from
   this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

</details>

<details title="Fazer download e testar o sistema agora mesmo" align='left'>
<br>
<summary align='left'><strong>Fazer download e testar o sistema agora mesmo</strong></summary>

No [final deste arquivo](https://github.com/hexagonix/hexagonix/blob/main/README.pt.md#como-testar-o-hexagonix-ou-o-andromeda) você encontra um tutorial para executar o Hexagonix/Andromeda em seu computador, tanto em uma versão virtualizada como de forma nativa. Lembre-se que é necessário possuir um computador de arquitetura x86 ou um emulador, caso esteja utilizando um dispositivo de outra arquitetura para testes.

Você pode ir até a sessão de [lançamentos](https://github.com/hexagonix/hexagonix/releases) para obter as versões estáveis do sistema. Você pode acessar o arquivo de [anúncio de versões](REL.pt.md) do Hexagonix/Andromeda. Sempre que possível, obtenha o último lançamento e realize o download das imagens .img disponíveis ou do pacote completo em formato zip. As versões disponíveis diretamente neste repositório são sempre versões de desenvolvimento (beta e release candidate), que também podem ser executadas e estão minimamente funcionais. Ao final de cada ciclo de desenvolvimento, as versões finais estarão disponíveis na sessão [lançamentos](https://github.com/hexagonix/hexagonix/releases).

</details>

<details title="Documentação do sistema" align='left'>
<br>
<summary align='left'><strong>Documentação do sistema</strong></summary>


* [Documentação do sistema (em construção)](https://github.com/hexagonix/Doc)

</details>

<details title="Ajude no desenvolvimento do Hexagonix/Andromeda" align='left'>
<br>
<summary align='left'><strong>Ajude no desenvolvimento do Hexagonix/Andromeda</strong></summary>

Se você tem conhecimento em criar código em Assembly x86 e gostaria de ajudar no desenvolvimento do sistema, sinta-se a vontade em me enviar um email! Veja [aqui](https://github.com/hexagonix/hexagonix/blob/main/README.pt.md#autor--contato) como entrar em contato comigo!

</details>

<details title="Reporte erros no sistema" align='left'>
<br>
<summary align='left'><strong>Reporte erros no sistema</strong></summary>

Você pode reportar erros do sistema [aqui](https://github.com/hexagonix/hexagonix/blob/main/README.pt.md#reportar-erros).

</details>

<hr>

# Sobre o sistema

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix.png" width="250" height="250">
</p>

<details title="Desenvolvimento" align='left'>
<br>
<summary align='left'><strong>Desenvolvimento</strong></summary>

O Hexagonix/Andromeda e todos os seus componentes vêm sendo desenvolvidos desde 2015 e foram escritos completamente em linguagem Assembly.

</details>

<details title="Por que dois nomes? Hexagonix e Andromeda, o quê são?" align='left'>
<br>
<summary align='left'><strong>Por que dois nomes? Hexagonix e Andromeda, o quê são?</strong></summary>

No início, o Andromeda foi planejado para ser um sistema operacional completo, composto pelo kernel, bibliotecas, interface gráfica e de texto e utilitários. Mais tarde, com o passar do tempo e a mudança na abordagem da arquitetura e objetivos do sistema, os componentes foram separados e se tornaram projetos independentes a nível de funcionamento, organização e desenvolvimento. Como será possível observar a diante, o núcleo do Andromeda foi separado do restante da árvore de código do Andromeda, se tornando um projeto independente, recebendo até um nome, Hexagon. A partir de então, surgiu a ideia de flexibilizar a composição do sistema e permitir o desenvolvimento de distribuições, como ocorre no GNU/Linux. Desta forma, distribuições do Hexagon poderiam ser criadas, agrupando os componentes necessários para o funcionamento básico (Hexagonix) e permitindo a extensão do sistema caso seja necessário, com novos componentes, módulos e utilitários, sendo o userland definido a cada caso. Com a mudança de arquitetura do próprio sistema, com o núcleo se aproximando de uma arquitetura semelhante ao Unix, novos utilitários no estilo e sintaxe Unix foram desenvolvidos e mantidos separados, em um outro projeto. Do projeto Andromeda original temos os aplicativos e bibliotecas gráficas específicas do Andromeda. Foi então criado um sistema base, que por si só já pode ser executado plenamente, e se transformou na base do Andromeda. Esse sistema base se chama Hexagonix, e é composto pelo carregador de inicialização HBoot, pelo kernel Hexagon, pelo shell, bibliotecas de ambiente Unix (aqui denominado ambiente Hexagonix) e utilitários Unix. Esse sistema é plenamente funcional, mas carece de recursos gráficos e aplicativos desenvolvidos para o ambiente Andromeda. Dessa forma, o Andromeda se destaca por ser uma camada a mais construída sobre a base do Hexagonix, com recursos gráficos, uma biblioteca gráfica e utilitários que funcionam sobre o Hexagonix e estendem sua função. Esse ambiente construído foi nomeado de ambiente Andromeda. Para suprir diferentes necessidades, as duas distribuições serão sempre mantidas. Ambas as versões são funcionais e podem ser utilizadas, dependendo do uso final desejado. Em resumo, tanto o Hexagonix quanto o Andromeda são distribuições do kernel Hexagon, diferindo quanto aos componentes incluídos.

Para compreender melhor esse modelo de distribuição, um exemplo adequado seria o que ocorre com o macOS (Apple)[^1]. O macOS é um sistema operacional Unix-like constrúido sobre o Darwin, um sistema operacional livre composto pelo kernel XNU, bibliotecas e utilitários, adicionando sobre o Darwin a interface gráfica Aqua e demais aplicativos e utilitários desenvolvidos pela Apple e outros fornecedores. O ambiente Darwin é facilmente acessado e observado através do macOS, como na utilização do terminal, por exemplo. O Darwin é um sistema completo e funcional, mas carece de alguns recursos gráficos, por exemplo, que só são distribúidos juntamente ao macOS. Nessa analogia, temos o macOS como Andromeda e Darwin como Hexagonix. 

</details>

<details title="E o código-fonte?" align='left'>
<br>
<summary align='left'><strong>E o código-fonte?</strong></summary>

O código-fonte do projeto já foi disponibilizado publicamente. O código do kernel e dos utilitários Unix-like e aplicativos Andromeda estão disponíveis, assim como o pacote de fontes que compõe o HBoot. As imagens de disco, tanto com o Hexagonix quanto com o Andromeda, já estão disponíveis e sua distribuição é livre. Observe a [licença](LICENSE) disponível neste repositório para mais informações. Vale ressaltar que a licença de cada pacote de código que compõe o sistema (Hexagon, HBoot, utilitarios Hexagonix, utilitários Andromeda, fontes e outros componentes) pode variar. Cada pacote pode ser liberado com um tipo de licença diferente (como GPL, MIT ou BSD, por exemplo). Fique atento a cada licença nos respectivos repositórios. Os componentes que não estão disponíveis no repositório oficial ainda se encontram em código fechado, regidos por uma licença proprietária Hexagonix, que pode ser encontrada [aqui](https://github.com/hexagonix/Doc/blob/main/LICENSES/Hexagonix).

</details>

<details title="A história do Hexagonix/Andromeda" align='left'>
<br>
<summary align='left'><strong>A história do Hexagonix/Andromeda</strong></summary>

O Andromeda começou como uma implementação em estrutura similar a sistemas do tipo DOS, com um interpretador com comandos internos com nomes, sintaxes e resultados semelhantes a um DOS genérico. O interpretador de comandos apresentava comandos de manipulação de arquivos e outros internamente, como em sistemas DOS convencionais. As unidades de disco também eram definidas como letras. Mais tarde, surgiu um interesse crescente e fascínio no funcionamento de sistemas Unix e todo o código foi reescrito ou adaptado para tornar o kernel do Sistema um kernel Unix-like. Todos os componentes do Sistema, assim como no DOS, eram mantidos em uma única árvore até então. Com a versão 1.5 do Andromeda, com nome de código "Unix-like", o kernel foi bastante modificado e reescrito para se adequar à filosofia Unix. As mudanças incluíram até mesmo a forma como os dispositivos eram tratados, com a escrita de uma camada de abstração de hardware com o gerenciamento de dispositivos como arquivos, além da adição das chamadas de sistema abrir(), fechar(), escrever() e ler(). Também foram escritos os utilitários base Unix, com a retirada de comandos do interpretador padrão, que foi reescrito para dar lugar a um shell Unix-like. Os camandos internos foram movidos para os utilitários, que passaram a contar com estrutura e sintaxe no estilo Unix. O restante dos utilitários, como mount, foi escrita, já tirando proveito da chamada abrir(), que também é utilizada para montar volume, além de abrir arquivos ordinários do volume. A chamada abrir() também é utilizada para iniciar outros periféricos, como portas seriais e paralelas. A chamada escrever() também funciona com dispositivos e arquivos, bem como fechar(). Foi também introduzido um VFS (Virtual File System), que suportará no futuro vários sistemas de arquivos e que torna transparente para o Sistema, programadores e usuários o gerenciamento de arquivos. Também foram incluídas novas funções de gerenciamento de hardware e muitos aprimoramentos e correções de bugs. O Sistema ganha novos utilitários Unix até o presente momento. Após essa alteração da proposta e arquitetura, os componentes foram separados e alocados em projetos específicos. A união destes componentes forma o sistema operacional. No caso do Hexagonix, temos o HBoot, Hexagon, shell, bibliotecas e aplicativos Unix, enquanto o Andromeda estende o Hexagonix, incorporando outras bibliotecas e aplicativos que as utilizam.

</details>

<hr>

# Componentes do sistema

<details title="Saturno" align='left'>
<br>
<summary align='left'><strong>Saturno</strong></summary>

O primeiro componente do Hexagonix/Andromeda é o Saturno. Ele é responsável por receber o controle do processo de inicialização realizado pelo BIOS/UEFI e procurar no volume o segundo estágio de inicialização. Para isso, ele implementa um driver para leitura de um sistema de arquivos FAT16. O segundo estágio de inicialização (ver adiante) pode implementar drivers para outros sistemas de arquivos e é responsável por encontrar o Hexagon, carregar módulos HBoot ou carregar um sistema do tipo DOS compatível (versão BETA).

</details>

<details title="Hexagon Boot (HBoot)" align='left'>
<br>
<summary align='left'><strong>Hexagon Boot (HBoot)</strong></summary>

O Hexagon Boot (HBoot) é um componente desenvolvido para permitir a inicialização do kernel Hexagon. Até então, a inicialização era realizada por apenas um estágio, que definia um ambiente bem básico, carregava o Hexagon na memória e imediatamente o executava, fornecendo um conjunto bem limitado de parâmetros. Isso se deve ao fato de que o código desse estágio fica restrito a 512 bytes, o que limita a realização de diversos testes e processamento de dados. Como o HBoot, foi possível expandir o número de tarefas realizadas antes da execução do Hexagon, além da possibilidade de fornecer mais informações a respeito do ambiente do dispositivo e de inicialização. Isso é particularmente importante para permitir a criação de uma árvore de dispositivos que pode ser utilizada pelo Hexagon para decidir como manipular cada dispositivo identificado. O HBoot é capaz de verificar quais unidades de disco estão disponíveis na máquina, emitir um tom de inicialização, obter a quantidade de memória RAM disponível instalada e permitir ou não o prosseguimento do processo de boot de acordo com essa informação. Caso nenhuma interação do usuário seja detectada (em um tempo de 3 segundos após a inicialização do HBoot e exibição de mensagens ao usuário), o HBoot irá realizar testes adicionais para verificar a capacidade do dispositivo em executar o sistema e irá carregar e executar o Hexagon (presente em um arquivo no volume nomeado de **HEXAGON.SIS**). Após o carregamento, o HBoot transfere o controle para o Hexagon, que é inicializado e armazena no ambiente do kernel os dados fornecidos pelo HBoot.

### Como interagir com o HBoot

A interação com o HBoot se dá pelo pressionamento da tecla F8 após a inicialização e exibição de mensagens na tela. O HBoot aguarda por 3 segundos alguma intereação e, caso nenhuma tenha ocorrido, continua a executar o protocolo de boot. A interação com o HBoot pode ser interessante para carregar módulos no formato HBoot, fornecer parâmetros de inicialização ao Hexagon, carregar algum sistema do tipo DOS cujos arquivos estejam presentes no mesmo volume ou ainda carregar imagens HAPP de outros núcleos (caso o desenvolvedor deseje utilizar a implementação HBoot em seu projeto). Abaixo, veja mais alguns detalhes de funções adicionais e de diagnóstico que podem ser realizadas via interação com o HBoot antes do carregamento do Hexagonix.


<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/HBoot.png" width="600" height="500">
</p>

### Outras funções disponíveis (módulos HBoot e modDOS)

#### Módulos HBoot

O HBoot permite o carregamento de módulos no formato HBoot, que podem ser úteis, no futuro, para permitir testes de hardware, como testes de memória e disco, caso os módulos estejam disponíveis no disco. Os módulos podem ser utilizados também para estender as funções do HBoot. A especificação do formato já está disponível e um exemplo pode ser encontrado abaixo. Esses módulos podem ser utilizados para testar dispositivos específicos, obter informações do hardware ou carregar arquivos em sistemas de arquivos não suportados originalmente pelo HBoot.

##### Módulos HBoot já implementados

Módulos HBoot vêm sendo desenvolvidos para estender a funcionalidade do HBoot. Até o momento, estes são:

* Spartan: implementação modelo de um módulo HBoot. Exibe uma mensagem na tela e solicita ao usuário o pressionamento de qualquer tecla para reiniciar o computador e iniciar o Hexagonix.
* x86-Detect: módulo de diagnóstico e inicialização do hardware do computador. Esse módulo detecta unidades de armazenamento disponíveis, verifica requisitos mínimos do computador para a execução do Hexagon (como memória RAM e processador), detecta e inicializa portas seriais e paralelas e exibe para o usuário se o dispositivo pode ou não executar o Hexagonix. Futuramente, será utilizado para encontrar outros sistemas operacionais instalados, realizar o teste de memória RAM e de desempenho de discos e encontrar e configurar dispositivos PCI. Uma entrada de inicialização rápida ao x86-Detect pode ser adicionada de forma permanente no HBoot, para execução mais fácil e com menos passos.

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/x86-Detect.png" width="600" height="500">
</p>

#### Carregar um sistema operacional do tipo DOS com modDOS

No contexto do desenvolvimento do Hexagonix, o HBoot também pode carregar e executar o núcleo do sistema operacional de código livre FreeDOS[^2], para que ferramentas utilitárias já estabelecidas e robustas que sejam executadas em ambiente DOS possam ser executadas sobre o volume e arquivos Hexagonix/Andromeda. Essa função é realizada por um módulo HBoot (modDOS) que, até esse momento, se integra ao HBoot como uma biblioteca de módulo, já contendo toda a estrutura necessária para ser um módulo independente. Futuramente, o plano é que essa biblioteca/módulo seja removida do HBoot e mantida como um módulo separado, removendo a complexidade e o código do HBoot. Por desempenho, neste momento, o modDOS ainda é mantido na árvore de código do HBoot. O FreeDOS foi escolhido devido a diversas características interessantes que facilitam a implementação necessária no modDOS. Primeiramente, o kernel do sistema está contido em um único arquivo, geralmente "KERNEL.SYS"[^3] (embora que no contexto do modDOS, o nome de arquivo não é importante, visto que a inicialização não se dará pelo inicializador do projeto FreeDOS, que espera encontrar um arquivo com este nome), além da sua distribuição livre e gratuita. Já outros sistemas do tipo DOS, como o MS-DOS (principalmente em sua versão anterior a 7.0), podem utilizar mais de um arquivo no disco, bem como exigem que estes arquivos estejam em locais definidos e sejam contíguos no disco. Essa obrigatoriedade de localização definida não pode ser atendida aqui, visto que a instalação de uma cópia do sistema DOS ocorre já em uma partição Hexagonix. A instalação de um sistema DOS é opcional e o modDOS torna a execução deste tipo de sistema mais fácil, sendo necessária apenas a cópia do kernel, interpretador de comandos  demais utilitários desejados a uma partição do Hexagonix. Além disso, a utilização de um sistema de distribuição livre remove qualquer problema de licenciamento. A instalação de um sistema DOS juntamente ao Hexagonix/Andromeda permite que ferramentas DOS sejam utilizadas para realizar tarefas específicas deste ambiente ou adicionar funções e utilitários que ainda não estão disponíveis ou terminados para serem utilizados no Hexagonix, como um utilitário de particionamento de disco, por exemplo [^4]. Caso os componentes de sistema do FreeDOS não estejam presentes no disco (a cópia dos arquivos do FreeDOS não faz parte da imagem e instalação padrão), a inicialização em modo de compatibilidade DOS não irá ocorrer.

### Exemplo de módulo HBoot

Abaixo é possível encontrar um exemplo de implementação de módulo HBoot (especificação de módulo HBoot v2.0):

```assembly
;;************************************************************************************
;;
;;    
;;                                Módulo do HBoot
;;        
;;                             Hexagon® Boot - HBoot
;;           
;;                 Copyright © 2020-2022 Felipe Miguel Nery Lunkes
;;                         Todos os direitos reservados
;;                                  
;;************************************************************************************

use16

;; O módulo deve apresentar um cabeçalho especial de imagem HBoot
;; São 6 bytes, com assinatura (número mágico) e arquitetura alvo

cabecalhoHBoot:

.assinatura:  db "HBOOT"       ;; Assinatura, 5 bytes
.arquitetura: db 01h           ;; Arquitetura (i386), 1 byte
.versaoMod:   db 01h           ;; Versão, com 1 byte
.subverMod:   db 00h           ;; Subversão, com 1 byte
.nomeMod:     db "NOME    "    ;; Nome do módulo, com 8 bytes

;; Configurar pilha e ponteiro

    cli            ;; Desativar interrupções
    
    mov ax, 0x2000 ;; Definir aqui os registradores de pilha
    mov ss, ax
    mov sp, 0
    
    sti            ;; Habilitar interrupções
     
    clc 

    mov ax, 0x2000 ;; Definir aqui os registradores de segmento
    mov ds, ax
    mov es, ax
    
    sti            ;; Habilitar as interrupções

;; Seu código aqui

```

### Sistemas de arquivos suportados

* FAT16B
* FAT12 (em desenvolvimento)

Novos sistemas de arquivos serão implementados no futuro, incluindo o suporte destes por meio de módulos HBoot.

### Reportar bugs

O HBoot ganhou muita complexidade desde o início de seu desenvolvimento, em 2020. Devido a esse aumento de código e a natureza de sua operação (16-bit), bugs podem ser encontrados. Os mesmos podem ser reportados no repositório ou por email, disponível no final deste arquivo.

</details>

<details title="Kernel Hexagon" align='left'>
<br>
<summary align='left'><strong>Kernel Hexagon</strong></summary>

### O que é

O Hexagon é um núcleo (kernel) monolítico executado em modo protegido 32-bit, desenvolvido tendo como alvo a arquitetura PC (x86). É um kernel escrito do zero, visando a velocidade e a compatibilidade de harware moderno mas também sendo capaz de ser executado em hardware mais antigo (como um Pentium III). No momento, garante um ambiente monoutilizador, apesar do uso de terminais virtuais, e monotarefa, apesar da capacidade de carregar, manter em memória e controlar mais de um processo, em uma pilha de execução. Futuramente, o kernel poderá receber suporte a execução de múltiplos processos em multitarefa preemptiva. O Hexagon é um kernel Unix-like e tenta implementar uma compatibilidade POSIX, embora longe desta, e compõe a base do Sistema Operacional Hexagonix/Andromeda, embora independente deste. Ele executa imagens executáveis no formato HAPP, desenvolvido exclusivamente para o Hexagon. O Hexagon também implementa uma API bastante sofisticada acessível através de uma chamada de sistema.

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/LogoHexagon.png" width="250" height="250">
</p>

### História

O kernel foi inicialmente desenhado e escrito visando uma estrutura e funcionamento próximos de sistemas DOS (Disk Operating System), como MS-DOS, nos ano de 2015 a 2017. Sendo assim, muitas chamadas de sistema e nomes de dispositivo seguiam uma sintaxe e nomes DOS. Com o passar do tempo, houve o interesse de aproximar o então núcleo do Andromeda, que a essa altura não possuia nome e era mantido junto ao código da distribuição, a uma estrutura e funcionamento mais próximos de sistemas do tipo Unix, como BSD ou Linux, por exemplo. Desta forma, muitas partes do kernel foram reimplementadas tendo em mente o novo objetivo. O código do núcleo foi separado do restante do Sistema e se tornou independente, em questão de desenvolvimento e também de funcionamento, além de ganhar um nome, Hexagon. Foi escrita uma camada de abstração de hardware com a inclusão de chamadas de sistema conhecidas no mundo Unix, como abrir(), fechar(), ler() e escrever()[^5]. Os dispositivos ganharam nome e as unidades de disco mudaram da nomenclatura DOS e foram para nomes de dispositivo Unix. O kernel então passa a seguir um processo de inicialização conhecido, com a execução, com PID 1, do primeiro processo do usuário, init, que então carrega o restante dos componentes. Foram então escritos utilitários Unix-like que passassem a utilizar a API Unix-like do kernel, e várias ferramentas Unix-like já foram escritas desde então (2017 em diante).

### O formato executável HAPP

O formato de imagem executável HAPP foi desenvolvida para o Hexagon para permitir o desenvolvimento de imagens que possam ser verificadas e validadas quanto a arquitetura e versões mínimas do kernel necessárias para a correta execução. O cabeçalho também armazena informações importantes, permitindo ao desenvolvedor adicionar diretamente um ponto de entrada, independente de onde ele esteja no interior da imagem, algo que deveria ser redirecionado anteriormente, quando a imagem executável era no formato binário puro. A imagem HAPP também permite validar se a imagem a ser carregada é realmente uma imagem executável, impedindo então que arquivos não suportados sejam executados, mesmo que não se tratem sequer de arquivos executáveis. Também permite que o sistema verifique as dependências do código, como a já citada arquitetura, bem como os números de versão do Hexagon, que devem ser iguais ou superiores ao mínimo especificado pelo cabeçalho. Todas as imagens HAPP devem apresentar este cabeçalho completo, incluindo as sessões reservadas, a fim de funcionarem corretamente em versões posteriores do Sistema. As imagens HAPP são sempre 32-bit. Para imagens 16-bit, o sistema utiliza a implementação de cabeçalho HBoot (implementação encontrada em módulos de inicialização do sistema).

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

Os aplicativos para Hexagonix/Andromeda podem ser desenvolvidos em Assembly, até o momento, utilizando o montador de sua preferência (desde que consiga gerar código x86). Bibliotecas para o desenvolvimento de aplicativos, contendo macros, funções e chamadas de sistema, podem ser encontradas [aqui (libasm)](https://github.com/hexagonix/libasm) e foram desenvolvidas para funcionar com os montadores [fasm](https://flatassembler.net/) e [nasm](https://www.nasm.us/). Ao acessar o repositório da **libasm**, você terá acesso às bibliotecas divididas de acordo com o suporte a um montador específico. O suporte a mais montadores pode ser adicionado no futuro. Uma biblioteca C (libc) também está nos planos para um futuro próximo.

Abaixo, uma implementação de um pequeno aplicativo escrito como exemplo, que utiliza o cabeçalho e chamadas de sistema do Hexagon, escrito em linguagem Assembly x86 em sintaxe Intel e montada com o auxílio do flat assembler (FASM). Note que para solicitar o acesso às chamadas do Hexagon, este aplicativo deve importar o arquivo **hexagon.s** da libasm (a depender do montador escolhido. Neste caso, fasm/hexagon.s). Este aplicativo envia uma mensagem ao terminal e se encerra em seguida. Você pode obter mais informações sobre a especificação do formato HAPP na biblioteca HAPP da [libasm para fasm](https://github.com/hexagonix/libasm/blob/main/fasm/HAPP.s) ou [libasm para nasm](https://github.com/hexagonix/libasm/blob/main/nasm/HAPP.s). Abaixo, você poderá obter mais informações sobre as chamadas de sistema.

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

format binary as "app" ;; Define o formato e extensão do arquivo gerado

use32

;; O cabeçalho pode ser definido diretamente assim e preenchido manualmente
;; ou através de um macro disponível na biblioteca HAPP.s, da libasm.
;; Abaixo, a implementação manual (que deve ser desencorajada, uma vez que 
;; alterações na API levariam a alterações manuais em todos os fontes. Isso
;; não ocorre com a utilização da biblioteca, que, ao ser atualizada, passa
;; a tornar compatíveis todos os fontes, automatizando o processo).

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

include "hexagon.s" ;; Incluir as chamadas de sistema

;;*************************************************************

;; Variaveis e constantes

msg: db 10, 10, "Este e um template com um exemplo de aplicativo HAPP simples!", 10, 0

;;*************************************************************

;; Ponto de entrada

inicioAPP:

    mov esi, msg

    imprimirString ;; Aqui temos um macro que configura e chama uma função da API

    Hexagonix encerrarProcesso ;; Outro macro que solicita qual chamada realizar
```

Uma documentação mais detalhada do Hexagon está em preparação e está sendo liberada conforme pronta.

### Chamadas de sistema

As chamadas de sistema são realizadas no estilo BSD, com o número da função presente na pilha e os parâmetros/argumentos junto aos registradores. Para uma lista completa de chamadas de sistema disponíveis na versão atual do sistema, dê uma olhada na biblioteca do Hexagon na [libasm para fasm](https://github.com/hexagonix/libasm/blob/main/fasm/hexagon.s) ou [libasm para nasm](https://github.com/hexagonix/libasm/blob/main/nasm/hexagon.s).

</details>

<details title="Ambiente Hexagonix" align='left'>
<br>
<summary align='left'><strong>Ambiente Hexagonix</strong></summary>

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

Alguns aplicativos e utilitários foram desenvolvidos exclusivamente para o Hexagonix, como:

* atop (versão alternativa de top)
* energia (controle de estado do computador)
* fnt (utilitário de alteração de fonte gráfica do Hexagonix)
* hash (shell alternativo)
* log (utilizado para obter logs internos do Hexagon, mas já obsoleto)
* lshapp (obtém e exibe informações de imagens HAPP)
* lshmod (obtém e exibe informações de módulos HBoot e do próprio HBoot)

Vale lembrar que os utilitários do Hexagonix tentam implementar uma interface POSIX na medida do possível, se assemelhando em sintaxe aos utilitários Unix (FreeBSD e Linux utilizados como modelo).
### Aplicativos de terceiros disponíveis para o Hexagonix

* [Flat Assembler (fasm)](https://flatassembler.net/index.php)

O Hexagonix recebeu um port do montador [Fasm](https://flatassembler.net/index.php), que foi adaptado para o Hexagonix, permitindo ao usuário desenvolver aplicativos diretamente no sistema. Este port é chamado de fasmX. As alterações adicionadas ao código, assim como licença do software, podem ser encontradas no [repositório do fasm para o Hexagonix](https://github.com/hexagonix/fasm). Este repositório é um fork do [repositório original](https://github.com/tgrysztar/fasm). O código adicionado é baseado em modificações realizadas do código original e adições autorais. Esse código modificado/autoral pode ser encontrado no repositório, [clicando aqui](https://github.com/hexagonix/fasm/tree/master/SOURCE/HEXAGONIX). O fasmX, port do fasm para Hexagonix, sempre é atualizado quando novidades são adicionadas no repositório do fasm. Para indicar que se trata de uma versão estável e testada, o número de versão do fasmX sempre herda a numeração do fasm, sucedido por um caractere x (como exemplo, a versão baseada no fasm 1.73.30, após teste, recebe a numeração 1.73.30x). Você pode reportar bugs ou problemas de geração ou otimização de código na versão para Hexagonix [aqui](https://github.com/hexagonix/fasm/issues). Para reportar erros gerais do fasm, utilize o repositório [oficial](https://github.com/tgrysztar/fasm).

</details>

<details title="Ambiente Andromeda" align='left'>
<br>
<summary align='left'><strong>Ambiente Andromeda</strong></summary>

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

</details>

<details title="Fontes gráficas do Hexagonix" align='left'>
<br>
<summary align='left'><strong>Fontes gráficas do Hexagonix</strong></summary>

A instalação padrão do Hexagonix também fornece uma série de fontes que podem ser carregadas pelo aplicativo de configurações ou utilitário de fontes (gerenciador de fontes). Esses arquivos são utilizados para alterar a fonte de exibição em modo gráfico do Hexagonix e Andromeda.

As fontes de modo gráfico para Hexagon são desenvolvidas como um bitmap em Assembly que, compiladas, geram uma imagem binária da fonte com representações de cada caractere. Os códigos das fontes padrão do Hexagonix já foram liberados como código livre e estão disponíveis no [repositório de fontes do Hexagonix](https://github.com/hexagonix/Fontes). 

### Como criar sua própria fonte gráfica

Sinta-se a vontade para realizar o download da fonte [modelo](https://github.com/hexagonix/Fontes/blob/main/modelo.asm), que já vem estruturada mas com os caracteres em branco, e desenhar a sua própria fonte gráfica! Para isso, você precisa saber algumas informações técnicas sobre elas:

* As fontes apresentam um altura de 16 e largura de 8 pixels. Essa informação é necessária para garantir que a sua fonte não apresente problemas durante o uso.
* Você pode dividir livremente os espaços reservados para acentuação e outras características gráficas de cada caractere, como cedilha ou porções que ficam abaixo da linha de caracteres, como y, vírgula e etc.
* As fontes são desenhadas no formato bitmap. Sendo assim, cada caractere é um mapa de pixels composto de 0s e 1s. Os 0s simbolizam áreas que não serão exibidas do caractere, enquanto os 1s representam os pixels do caractere que serão exibidos ao usuário. Você deve alterar cada matriz de caractere na fonte modelo adicionando os 1s onde deseja que os pixels sejam exibidos para formar o caractere. Abaixo, você verá um exemplo de um caractere em branco e a mesma representação deste caractere pronto para a fonte.

O código abaixo mostra a representação em bitmap da cerquilha (#) na fonte [modelo](https://github.com/hexagonix/Fontes/blob/main/modelo.asm) e a implementação na fonte [hint](https://github.com/hexagonix/Fontes/blob/main/hint.asm).

```assembly
;; Representação em branco do caractere cerquilha (#), no modelo 

.cerquilha: 

	db 00000000b ;; Dois pixels de altura para caracteres acima da letra
	db 00000000b
	
	db 00000000b
	db 00000000b
	db 00000000b
	db 00000000b
	db 00000000b
	db 00000000b
	db 00000000b
	db 00000000b
	db 00000000b

	db 00000000b ;; Cinco pixels de altura para caracteres acima da letra
	db 00000000b
	db 00000000b
	db 00000000b
	db 00000000b

;; Representação em branco do caractere cerquilha (#), na fonte hint 

.cerquilha: 

	db 00000000b
	db 00000000b
	
	db 00000000b
	db 00000000b
	db 00100010b
	db 00100010b
	db 01111111b
	db 00100010b
	db 01111111b
	db 00100010b
	db 00100010b

	db 00000000b
	db 00000000b
	db 00000000b
	db 00000000b
	db 00000000b

```

Você já deve conseguir visualizar, dentro da matriz, a cerquilha, marcada pela presença de 1s.

Você pode desenvolver quantas fontes quiser e brincar com designs diferentes e inovadores, bem como estender os caracteres disponíveis (utilizando a referência ASCII).

</details>

<details title="Bibliotecas de desenvolvimento do sistema" align='left'>
<br>
<summary align='left'><strong>Bibliotecas de desenvolvimento do sistema</strong></summary>


O Hexagonix/Andromeda também fornece funções que devem ser utilizadas para interagir com o próprio ambiente do sistema. As bibliotecas são utilizadas para acessar funções implementadas pelo Hexagon ou pelas próprias bibliotecas, permitindo o desenvolvimento facilitado de aplicativos e utilitários tanto para o ambiente Hexagonix quanto para o Andromeda. As bibliotecas implementam funções para exibição de texto, cálculos matemáticos, envio de mensagens, abertura de arquivos e dispositivos e muito mais. A biblioteca básica (hexagon.s) fornece funções acessíveis para ambos os ambientes possíveis de distribuição, enquanto outras bibliotecas podem ser exclusivas do ambiente Andromeda. Essas bibliotecas incluem funções gráficas para montar interfaces em modo gráfico (Andromeda), bem como funções para verificar a versão do sistema atualmente em execução (Hexagonix e Andromeda). Os utilitários base Hexagonix realizam a checagem da versão do Hexagon para verificar se podem ser executados, utilizando o utilitário Unix uname ou diretamente por uma chamada de sistema do Hexagon.

Para saber mais e verificar cada função disponível nas bibliotecas de desenvolvimento do sistema, veja o repositório da [libasm](https://github.com/hexagonix/libasm).

</details>

<hr>

# Como testar o Hexagonix ou o Andromeda

## Requisitos do sistema

Abaixo, uma lista de requisitos mínimos e recomendados para testar o Hexagonix/Andromeda em uma máquina virtual ou máquina física.

<details title="Requisitos mínimos" align='left'>
<br>
<summary align='left'><strong>Requisitos mínimos</strong></summary>

* Processador: Pentium III (1999) com suporte a SSE e MMX ou mais recente;
* Memória RAM: 32 Mb mínimo (uma instalação mínima com 32 Mb costuma ser suficiente, na maioria dos casos);
* Disco rígido: disco rígido IDE ou SATA com mínimo de 50 Mb;
* Periféricos necessários:
  * Porta serial (1-4);
  * Porta paralela (1-4);
  * Teclado PS/2 ou USB;
  * Placa de vídeo VGA com 2 Mb de memória de vídeo (com suporte a cores).

</details>

<details title="Recomendado" align='left'>
<br>
<summary align='left'><strong>Recomendado</strong></summary>

* Processador: Pentium D ou mais recente;
* Memória RAM: 50 Mb;
* Periféricos opcionais:
  * Mouse PS/2 ou USB;
  * Placa de vídeo com > 2 Mb de memória de vídeo.

</details>

## Obter as imagens de disco com a instação do sistema

Para testar o Hexagonix ou Andromeda, você vai precisar de uma das imagens de disco disponíveis neste repositório, bem como a ferramenta [qemu](https://www.qemu.org) instalada em seu computador, caso deseje testar o sistema em ambiente virtualizado. A imagem também pode ser utilizada para a gravação em um disco físico em uma máquina real.

Para testar o Hexagonix, obtenha o arquivo ['hexagonix.img'](hexagonix.img) neste repositório.
Para testar o Andromeda, obtenha o arquivo ['andromeda.img'](andromeda.img) neste repositório.

## Para o teste em ambiente virtualizado

Primeiramente, você deve instalar a ferramenta qemu, que irá gerenciar a máquina virtual. Para isso, você pode instalar o qemu utilizando repositórios oficiais de distribuições Linux ou acessando [aqui](https://www.qemu.org) para obter os arquivos de instalação para Windows e macOS.

<details title="Instalar no Debian, Ubuntu, Pop!_OS e derivados" align='left'>
<br>
<summary align='left'><strong>Instalar no Debian, Ubuntu, Pop_OS! e derivados</strong></summary>

Para o Ubuntu, a linha a seguir irá instalar o qemu e todas as suas dependências (privilégios de superusuário necessários):

```
sudo apt install qemu qemu-system-i386
```

</details>

Agora que você tem o qemu instalado em seu computador, você pode prosseguir com a execução do sistema.

Para executar o sistema de maneira satisfatória, você deve fornecer ao menos 32 MB de RAM para a máquina virtual. Isso se deve a arquitetura de gerenciamento de memória do Hexagon, que exige 16 MB de RAM exclusiva para o kernel a ao menos 16 MB para alocar os aplicativos, utilitários e arquivos abertos. O Hexagon não admite menos que isso para ser executado. Caso mais memória seja fornecida, a memória adicional será sempre reservada, com prioridade, para ser disponibilizada aos processos do usuário. Normalmente, a linha de comando abaixo cumpre todos os requisitos para a execução do sistema:

```
qemu-system-i386 -hda andromeda.img -m 32 -soundhw pcspk --enable-kvm -serial file:"Serial.txt"
qemu-system-i386 -hda hexagonix.img -m 32 -soundhw pcspk --enable-kvm -serial file:"Serial.txt"
```

Você pode omitir po parâmetro -serial caso queira. Esse parâmetro garante que a saída de debug do Hexagon e aplicativos serão direcionados para um arquivo em seu computador, onde você poderá consultar o que foi enviado. Você também pode omitir o parâmetro -soundhw, responsável por direcionar a saída de som do sistema virtual para seu computador físico. Em alguns sistema Linux, a configuração acima pode entrar em conflito com o pulseaudio, e pode ser omitida. Lembre-se que ao omitir o parâmetro, os sons do sistema não serão emitidos para você.

Lembrando que você deve utilizar uma versão/edição do qemu que consiga executar software escrito para a arquitetura x86 (i386 ou x86_64). Para realizar o download e instalação do qemu, clique [aqui](https://www.qemu.org/download/).

## Para teste em máquina física

Você deve utilizar o Linux/macOS ou alguma ferramenta disponível para o Windows que te permita gravar essa imagem em disco.

No Linux/macOS/Unix, use a linha abaixo:

```
dd if=andromeda.img of=/dev/unidade
```
onde unidade equivale ao dispositivo desejado (geralmente sdb ou sdc, em caso de dispositivos USB e hda, hdb, sda ou sdb, para unidades de disco rígido/estado sólido). Reinicie seu computador e teste o sistema. Vale lembrar que o modo de boot seguro não é suportado, além de que o boot só é suportado em BIOS ou no modo legado BIOS do UEFI.

Vale ressaltar que o desempenho do sistema pode variar de acordo com a máquina testada. Junta-se a isso o fato de que as versões mais recentes do sistema não foram ou estão sendo testadas diretamente na máquina física, como sistema operacional principal. Caso algum problema ocorra ao executar o Hexagonix/Andromeda em uma máquina física, por favor reporte o erro detalhado [aqui](https://github.com/hexagonix/Distro/issues), em português ou inglês, informando dados como marca do dispositivo, processador, quantidade de memória RAM, placa de vídeo (se disponível) e periféricos conectados, bem como o dispositivo utilizado para instalar o sistema (unidade de disco interna ou mídia removível USB).

## Primeiro uso

Ao iniciar o sistema, você deverá introduzir um nome de usuário e senha. Para o primeiro uso, utilize

```
Usuário: root
Senha: root
```

Você pode adicionar outro usuário alterando o arquivo 'USUARIO.UNX' na raiz do disco. Lembre-se de não remover o usuário raiz (root). Isso pode tornar o sistema inoperante de forma permanente.

<details title="Reportar erros" align='left'>
<br>
<summary align='left'><strong>Reportar erros</strong></summary>

Você pode reportar erros e ajudar a desenvolver o sistema. Para isso, abra uma notificação de erro [aqui](https://github.com/hexagonix/Distro/issues), informando o erro da forma mais detalhada possível (como marca do dispositivo, processador, quantidade de memória RAM, placa de vídeo e periféricos conectados, bem como o dispositivo utilizado para instalar o sistema, como unidade de disco interna ou mídia removível USB). Lembre-se de informar em qual aplicativo ocorreu o erro, caso o erro ocorra já com o sistema em operação. Caso o problema se dê no processo de inicialização, informe o que foi exibido/o comportamento observado da máquina.

</details>

<hr>

# Capturas de tela

<details title="Hexagonix" align='left'>
<br>
<summary align='left'><strong>Hexagonix</strong></summary>

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix1.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix2.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix3.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix4.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Hexagonix5.png" width="500" height="400">
</p>

Você pode ver mais [aqui](https://github.com/hexagonix/Distro/tree/main/Img).

</details>

<details title="Andromeda" align='left'>
<br>
<summary align='left'><strong>Andromeda</strong></summary>

<p align="center">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda1.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda2.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda3.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda4.png" width="500" height="400">
<img src="https://github.com/hexagonix/Doc/blob/main/Img/Andromeda5.png" width="500" height="400">
</p>

Você pode ver mais [aqui](https://github.com/hexagonix/Distro/tree/main/Img).

</details>

<hr>

# Outras informações

<details title="Idiomas" align='left'>
<br>
<summary align='left'><strong>Idiomas</strong></summary>

Neste momento, tanto o sistema quanto a documentação estão disponíveis apenas em português. O documentação em inglês estará disponível em breve, e há planos para suporte ao inglês como possibilidade de idioma principal, além do português (grande parte do trabalho já foi feita).

</details>

<details title="Inspirações" align='left'>
<br>
<summary align='left'><strong>Insipirações</strong></summary>

Este projeto foi possível e hoje consegue ver a luz do dia graças a muitos outros que já vieram antes e contribuiram com ideias de design e ensinando como deve funcionar um sistema operacional, mesmo que simples. São eles:

* MS-DOS, com código disponível [aqui](https://github.com/microsoft/MS-DOS)
* [MikeOS](http://mikeos.sourceforge.net/)
* [Linux 0.1.1](https://kernel.org)
* [FreeBSD](https://www.freebsd.org/)
* [XNU/Darwin](https://github.com/apple/darwin-xnu)
* [LittleKernel](https://github.com/littlekernel/lk)
* [Google Fuchsia](https://fuchsia.googlesource.com/fuchsia/)

Além disso, outros projetos auxiliaram no desenvolvimento do Hexagonix/Andromeda, seja fornecendo novas ideias de design que fogem da organização tradicional de um sistema operacional, seja fornecendo código bem documentado que permitia entender o funcionamento de certas partes de um sistema operacional, seja contribuindo com exemplos de código que mais tarde vieram a inspirar funções que foram escritas exclusivamente para o Hexagonix/Andromeda (principalmente o código do kernel). Apesar de não terem sido copiados e reutilizados no sistema, o código destes projetos de domínio público possibilitaram que o funcionamento de determinados componentes do computador fossem compreendidos, abrindo portas para que códigos autorais fossem escritos com base no estudo do código destes projetos. Vale ressaltar que os projetos abaixo foram liberados pelos seus desenvolvedores originais em domínio público. São eles:

* [Snowdrop OS](http://www.sebastianmihai.com/snowdrop/), que me inspirou a escrever várias rotinas de controle de hardware e outras funções 16-bit disponíveis no HBoot. O código deste sistema foi liberado em domínio público.
* [Alotware](https://github.com/0x5CE/alotware), que me inspirou a criar as funções de gerenciamento de processos nas versões iniciais do Hexagon (hoje, já reescritas inúmeras vezes). O código deste sistema foi liberado em domínio público.

</details>

<details title="Autor, contribuidores e contatos" align='left'>
<br>
<summary align='left'><strong>Autor, contribuidores e contatos</strong></summary>

## Autor

* [Felipe Miguel Nery Lunkes](https://github.com/felipenlunkes)
## Contribuidores

* [Felipe Miguel Nery Lunkes](https://github.com/felipenlunkes)

## E-mail

* hexagonixdev@gmail.com (PT/EN) 
* felipemiguel_nery@hotmail.com (PT/EN)

## Redes sociais

* [Twitter](https://twitter.com/felipeldev) (Felipe Miguel Nery Lunkes)

</details>

<details title="Notas de direitos autorais" align='left'>
<br>
<summary align='left'><strong>Notas de direitos autorais</strong></summary>

O Hexagonix/Andromeda foi desenvolvido do zero por [Felipe Lunkes](https://github.com/felipenlunkes).

Leia a [licença](LICENSE) para mais informações sobre direitos autorais, propriedade de código e redistribuição que se aplicam apenas aos arquivos disponíveis neste repositório (não se aplicam ao conjunto de arquivos de dados e de código fonte que compõem o Hexagonix/Andromeda). Vale ressaltar que o código dos componentes do sistema estão sendo liberados aos poucos e que cada pacote pode ser liberado com uma licença diferente. Sempre fique atento ao arquivo 'LICENSE' disponível em casa repositório para estar ciente dos direitos e obrigações legais.

</details>

[^1]: Você pode obter mais informações sobre a relação entre o Darwin e o macOS [aqui](https://pt.wikipedia.org/wiki/Darwin_(sistema_operacional)).
[^2]: Você pode encontrar a página do projeto [aqui](https://www.freedos.org/).
[^3]: A inicialização em modo DOS foi possível após pesquisa na documentação do FreeDOS, especialmente no arquivo "SYS.C" (que pode ser encontrado [aqui](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/dos/sys/2043/)), que indica em qual segmento o kernel espera ser carregado e quais parâmetros são necessários para inicializar o kernel corretamente. Cada sistema DOS apresenta um segmento de carregamento preferencial e esse carregamento de outras edições do DOS pode ser implementada futuramente com o auxílio de novos módulos HBoot (em caso de sistema proprietário, o usuário deverá ter uma licença). Todo o código para o carregamento do núcleo foi desenvolvido do zero e não se baseia em algum existente (a implementação do HBoot e do modDOS, que são originais, se dão em Assembly, enquanto o código de carregamento do FreeDOS é desenvolvido em C). A implementação original do código do modDOS e de outros módulos para sistemas DOS também livra a implementação de qualquer problema legal.
[^4]: A iniciação em modo de compatibilidade DOS do HBoot (modDOS) pode ser útil para rodar ferramentas de verificação de erros no volume, desfragmentação do volume, particionador e outras ferramentas de diagnóstico, bem como de desenvolvimento, como compiladores e montadores que não são suportados pelo Hexagonix/Andromeda (as ferramentas de 16 bits, por exemplo).
[^5]: Compatível com as chamadas open(), close(), read() e write(), pelo menos em conceito. As chamadas de sistema são realizadas sempre no estilo BSD, com número de função na pilha e parâmetros nos registradores.
