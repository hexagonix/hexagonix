# Andromeda
# Sistema Operacional Hexagonix/Andromeda

Seja bem-vindo ao Sistema Operacional Hexagonix/Andromeda

## Notas de direitos autorais 

O Hexagonix/Andromeda foi desenvolvido do zero por Felipe Lunkes (você pode o encontrar em github.com/felipenlunkes).

Sistema Operacional Andromeda. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. Todos os direitos reservados.
Kernel Hexagon. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. Todos os direitos reservados.
Gerenciador de Boot Saturno. Copyright © 2016-2022 Felipe Miguel Nery Lunkes. Todos os direitos reservados.
Hexagon Boot (HBoot). Copyright © 2020-2022 Felipe Miguel Nery Lunkes. Todos os direitos reservados.

## Antes de mais nada

No final deste arquivo você encontra um tutorial para executar o Hexagonix/Andromeda em seu computador, tanto em uma versão virtualizada como de forma nativa. Lembre-se que é necessário possuir um computador de arquitetura x86 ou um emulador, caso esteja utilizando um dispositivo de outra arquitetura para testes. 

* [Documentação do sistema (em construção)](https://github.com/hexagonix/Distro/Doc)

# Sobre o sistema

## Por que dois nomes? Hexagonix e Andromeda, o quê são?

No início, o Andromeda foi planejado para ser um sistema operacional completo, composto pelo kernel, bibliotecas, interface gráfica e de texto e utilitários. Mais tarde, com o passar do tempo e a mudança na abordagem da arquitetura e objetivos do sistema, os componentes foram separados e se tornaram independentes a nível de funcionamento e organização. Como será possível observar a diante, o núcleo do Andromeda foi separado do restante da árvore de código do Andromeda, se tornando um projeto independente, recebendo até um nome, Hexagon. Com a mudança de arquitetura do próprio sistema, com o núcleo se aproximando de uma arquitetura semelhante ao Unix, novos utilitários no estilo e sintaxe Unix foram desenvolvidos e mantidos separados, em um outro projeto. Do projeto Andromeda original temos os aplicativos e bibliotecas gráficas específicas do Andromeda. Foi então criado um sistema base, que por si só já pode ser exexutado plenamente, e se transformou na base do Andromeda. Esse sistema base se chama Hexagonix, e é composto pelo carregador de inicialização HBoot, pelo kernel Hexagon, pelo shell, bibliotecas de ambiente Unix e utilitários Unix. Esse sistema é plenamente funcional, mas carece de recursos gráficos e aplicativos desenvolvidos para o ambiente Andromeda. Dessa forma, o Andromeda se destaca por ser uma camada a mais sobre o Hexagonix, com recursos gráficos, uma biblioteca gráfica e utilitários que funcionam sobre o Hexagonix e estendem sua função. Ambas as versões são funcionais e podem ser utilizadas, dependendo do uso final desejado. Em resumo, tanto o Hexagonix quanto o Andromeda são distribuições do kernel Hexagon, diferindo quanto aos componentes incluídos.

Um exemplo adequado seria o que ocorre com o macOS (Apple). O macOS é um sistema operacional Unix-like constrúido sobre o Darwin, um sistema operacional livre composto pelo kernel XNU, bibliotecas e utilitários, adicionando sobre o Darwin a interface gráfica Aqua e demais aplicativos e utilitários desenvolvidos pela Apple e outros fornecedores. O ambiente Darwin é facilmente acessado e observado através do macOS, como na utilização do terminal, por exemplo. O Darwin é um sistema completo e funcional, mas carece de alguns recursos gráficos, por exemplo, que só são distribúidos juntamente ao macOS. Nessa analogia, temos o macOS como Andromeda e Darwin como Hexagonix. 

## E o código-fonte?

O código-fonte do projeto ainda não está disponível publicamente, mas deverá estar em um futuro próximo. Entretanto, a distribuição das imagens de disco, tanto com o Hexagonix quanto com o Andromeda, é livre. Observe a licença disponível neste repositório para mais informações.

## O Hexagonix/Andromeda:

O Sistema Operacional Hexagonix/Andromeda é uma coleção de peças de software que atua no gerenciamento do hardware do computador onde está instalado, permitindo o carregamento e funcionamento de aplicativos. Ele é composto por vários componentes, que atuam no processo de inicialização do computador, testes de recursos e carregamento do kernel (núcleo) do sistema operacional, uma interface de interação com o usuário e uma série de utilitários.
O Andromeda é uma distribuição que incorpora um kernel Unix-like, denominado Hexagon, bibliotecas de suporte, utilitários desenvolvidos exclusivamente para o ambiente Andromeda e utilitários Unix-like de linha de comando (estes últimos e o kernel Hexagon por si só já configuram um sistema operacional base, o Hexagonix).

## A história do Hexagonix/ Andromeda:

O Andromeda começou como uma implementação em estrutura similar a sistemas do tipo DOS, com um interpretador com comandos internos com nomes, sintaxes e resultados semelhantes a um DOS genérico. O interpretador de comandos apresentava comandos de manipulação de arquivos e outros internamente, como em sistemas DOS convencionais. As unidades de disco também eram definidas como letras. Mais tarde, surgiu um interesse crescente e fascínio no funcionamento de sistemas Unix e todo o código foi reescrito ou adaptado para tornar o kernel do Sistema um kernel Unix-like. Todos os componentes do Sistema, assim como no DOS, eram mantidos em uma única árvore até então. Com a versão 1.5 do Andromeda, com nome de código "Unix-like", o kernel foi bastante modificado e reescrito para se adequar à filosofia Unix. As mudanças incluíram até mesmo a forma como os dispositivos eram tratados, com a escrita de uma camada de abstração de hardware com o gerenciamento de dispositivos como arquivos, além da adição das chamadas de sistema abrir(), fechar(), escrever() e ler(). Também foram escritos os utilitários base Unix, com a retirada de comandos do interpretador padrão, que foi reescrito para dar lugar a um shell Unix-like. Os camandos internos foram movidos para os utilitários, que passaram a contar com estrutura e sintaxe no estilo Unix. O restante dos utilitários, como mount, foi escrita, já tirando proveito da chamada abrir(), que também é utilizada para montar volume, além de abrir arquivos ordinários do volume. A chamada abrir() também é utilizada para iniciar outros periféricos, como portas seriais e paralelas. A chamada escrever() também funciona com dispositivos e arquivos, bem como fechar(). Foi também introduzido um VFS (Virtual File System), que suportará no futuro vários sistemas de arquivos e que torna transparente para o Sistema, programadores e usuários o gerenciamento de arquivos. Também foram incluídas novas funções de gerenciamento de hardware e muitos aprimoramentos e correções de bugs. O Sistema ganha novos utilitários Unix até o presente momento. Após essa alteração da proposta e arquitetura, os componentes foram separados e alocados em projetos específicos. A união destes componentes forma o sistema operacional. No caso do Hexagonix, temos o HBoot, Hexagon, shell, bibliotecas e aplicativos Unix, enquanto o Andromeda estende o Hexagonix, incorporando outras bibliotecas e aplicativos que as utilizam.

## Versionalização do Hexagonix/Andromeda:

O sistema operacional apresenta uma numeração de versão independente dos componentes associados. Cada componente, desde o gerenciador de inicialização, até um simples utilitário, recebem uma numeração de versão independente e que reflete seu estado de desenvolvimento. Um número de versão do Hexagonix/Andromeda apresenta três conjuntos de números divididos em três blocos separados por um caractere de ponto ".". O primeiro deles representa o número principal de versão e se baseia no número um. Já o segundo número se refere ao lançamento, este é o número que varia de um lançamento do Hexagonix/Andromeda para outro e distingue entre as grandes versões do Sistema, além de ser utilizado como número de versão que é verificado pelos aplicativos e utilitários para verificar se a versão do sistema apresenta os requisitos mínimos para a execução do software. Já o terceiro é o número de revisão de cada grande lançamento e, caso seja 0, pode ser omitido, ficando a versão com apenas dois blocos de algarismos. Um exemplo seriam as versões "1.14.4", cuja versão base é sempre 1, até o momento, 14 indica o lançamento (este se refere, na maioria das vezes, a real versão do Sistema. Pense, por exemplo, no sistema de numeração da Apple com o Mac OS X/OS X/macOS até a versão 11.0 Big Sur, que começa sempre com 10 e é seguido do número do lançamento e revisão). Já o número 4 seria a revisão dentro do grande lançamento, que diz respeito a correção de bugs e adição de alguma funcionalidade que não mude de forma profunda o Sistema nem o uso do mesmo.

Normalmente, o Hexagonix e o Andromeda apresentam a mesma numeração de versão principal, mas isso não é necessariamente obrigatório. Os números de versão podem divergir em algum momento, bem como os componentes de cada distribuição. A versão do Hexagon, por exemplo, pode ser diferente mesmo em números de versão idênticos, mas esse tipo de divergência será sempre evitada.

# Componentes do sistema

## Um pouco sobre a inicialização do sistema:

Após a inicialização do firmware, o BIOS ou outro firmware, como UEFI em modo legado, realiza a busca de um volume/disco marcado como inicializável e, ao encontrar, carrega o primeiro setor para o endereço 0x7C00. No caso de um volume Hexagon, no primeiro setor do volume está localizado o componente denominado Saturno. Saturno é o gerenciador de inicialização MBR de um volume Hexagon e atua como primeiro estágio na cadeia de carregamento do Sistema. Ele realiza a procura, no volume, do segundo estágio, bem mais robusto, o Hexagon Boot (HBoot). O HBoot não apresenta as mesmas limitações do componente anterior, uma vez que não está restrito ao tamanho de 512-bytes. Ao iniciar, o HBoot realiza uma série de testes e diagnósticos da máquina, verificando quais discos/volumes estão disponíveis na máquina, qual a quantidade de memória RAM instalada e inicializando alguns periféricos, como portas seriais, além de verificar o processador instalado quanto a sua capacidade de executar o Hexagon. Caso a quantidade de memória RAM instalada seja menor que o mínimo, o processador não seja suportado ou ocorra algum erro em algum periférico essencial, a protocolo de inicialização é cancelado. Caso os testes sejam bem sucedidos, ocorre a procura, no volume, do arquivo que contêm o kernel Hexagon, com seu carragamento, construção de uma estrutura de parâmetros, configuração de registradores com informações básicas de hardware e posterior execução. O HBoot também é capaz de carregar e executar módulos no formato HBoot, bem como iniciar um sistema do tipo DOS cujos arquivos estejam presentes no volume Hexagon (até o momento, apenas o FreeDOS é suportado). Também é capaz de realizar alguns testes de hardware sob demanda, como som e gráficos. Após o carregamento do Hexagon, o kernel recebe o controle do dispositivo e realiza a configuração dos periféricos, constrói estruturas internas de controle e inicia o primeiro processo de usuário, com PID 1, normalmente o Inicializador do Sistema, ou init. O init irá ler o arquivo de configuração "INIT.UNX" no volume e iniciar os serviços lá descritos, geralmente o Gerenciador de Login e Usuários, ou simplemente login. Este, por sua vez, busca as informações em "USUARIO.UNX" e as compara com as entradas do usuário, e, caso as credenciais sejam válidas, inicia o primeiro shell ou utilitário descrito na entrada de usuário. Após, o Hexagon entra em modo administrativo e gerencia requisições dos aplicativos e periféricos, expondo a API para construção e execução dos demais componentes do Sistema (para mais informações, consulte o arquivo de cabeçalho "ANDRMDA.S", que já documenta a API).

## Ambiente Hexagonix:

O Hexagonix/Andromeda implementa uma série de utilitários Unix-like, com funcionalidade e sintaxe de uso semelhante à sistemas UNIX e Unix-like. Utilitários como init, login, sh, top, ps, cp, rm, cat, clear, man, dentre outros, estão inclusos na distribuição padrão do Hexagonix. Estes utilitários compõem o pacote de utilitários base do Hexagonix. As ferramentas de inicialização de ambiente de modo usuário e login estão neste pacote base Unix, bem como vários arquivos de configuração deste ambiente. Estes utilitários não apresentam uma interface gráfica, apenas uma interface em linha de comando (CLI). Entretanto, podem ser solicitados por aplicativos que apresentem interface gráfica.

## Ambiente Andromeda:

Além das ferramentas Unix, o Andromeda inclui aplicativos e utilitários que não implementam a filosofia Unix ou apresentam sintaxe e forma de uso bastante diferentes do que se esperaria de um ambiente Unix. Desta forma, eles são separados como aplicativos base Andromeda do Andromeda. Aqui estão o aplicativo de configurações do Sistema, calculadora, gerenciador de fontes, editores de texto e a IDE desenvolvida para o Andromeda. Estes utilitários podem ou não apresentar uma interface gráfica.

## Fontes do Hexagonix:


A instalação padrão do Hexagonix também fornece uma série de fontes que podem ser carregadas pelo aplicativo de configurações ou utilitário de fontes (gerenciador de fontes).

# Bibliotecas do Andromeda:

O Hexagonix/Andromeda também fornece funções que devem ser utilizadas para interagir com o próprio ambiente do sistema. Essas bibliotecas incluem funções gráficas para montar interfaces em modo gráfico (Andromeda), bem como funções para verificar a versão do sistema atualmente em execução (Hexagonix e Andromeda). Os utilitários base Hexagonix realizam a checagem da versão do Hexagon para verificar se podem ser executados, utilizando o utilitário Unix uname ou diretamente por uma chamada de sistema do Hexagon.

# Como testar o Hexagonix ou o Andromeda:

Para testar o Hexagonix ou Andromeda, você vai precisar de uma das imagens de disco disponíveis neste repositório, bem como a ferramenta qemu instalada em seu computador. A imagem também pode ser utilizada para a gravação em um disco físico em uma máquina real. 

Para testar o Hexagonix, obtenha o arquivo 'hexagonix.img' neste repositório.
Para testar o Andromeda, obtenha o arquivo 'andromeda.img' neste repositório.

## Para o teste em ambiente virtualizado

Você deve fornecer ao menos 32 MB de RAM para a máquina virtual. Normalmente, a linha de comando abaixo cumpre todos os requisitos para a execução do sistema:

qemu-system-i386 -hda andromeda.img -m 32 -soundhw pcspk
ou
qemu-system-i386 -hda hexagonix.img -m 32 -soundhw pcspk

Lembrando que vocÊ deve utilizar uma versão/edição do qemu que consiga executar software escrito para a arquitetura x86.

## Para teste em máquina física

Você deve utilizar o Linux/macOS ou alguma ferramenta Windows que te permita gravar essa imagem em disco.

No Linux/macOS/Unix, use a linha abaixo:

dd if=andromeda.img of=/dev/unidade, onde unidade equivale ao dispositivo desejado. Reinicie seu computador e teste o sistema. Vale lembrar que o modo de boot seguro não é suportado, além de que o boot só é suportado em BIOS ou no modo legado BIOS do UEFI.

# Idiomas

Neste momento, tanto o sistema quanto a documentação estão disponíveis apenas em português. O documentação em inglês estará disponível em breve, e há planos para suporte ao inglês como possibilidade de idioma principal, além do português (grande parte do trabalho já foi feita).

# Autor & contato

* [Felipe Miguel Nery Lunkes](https://github.com/felipenlunkes)

# E-mail:

hexagonixdev@gmail.com (PT/EN) 
felipemiguel_nery@hotmail.com (PT/EN)

Versão deste arquivo: 3.0
