# Routers Basic Cisco
## Linha de configuração básica dos roteadores cisco 
>
 > &gt; (modo usuário)
 >
 >#( modo privilegiado)
 >
 > (config)# (modo de configuração global)
 >
 >>Sub-modos de configuração
 >
> (config-if)# interface
>
> (config-router)# protocolo de roteamento dinâmico
>
> (config-line)# linha telnet (acesso remoto) e console
>
> Shift + control + 6 (interrompe comandos emitidos no terminal)

###  Configurando o nome
>Router &gt; enable
>
>Router # configure terminal
>
> Router(config)# hostname < Insiar o nome que  desejar do roteador >

### Configurando senha 
>Router(config) # enable password < Insira a senha que desejar >

### Configurando senha secret
>Router(config) # enable secret < Insira a senha que desejar >

### Configurando senha da console

>Router(config) # line console 0
>
>Router(config-line) # password ti-redes
>
>Router(config-line) # logging synchronous < Remove mensagens na tela>
>
>Router(config-line) # exec-timeout < tempo em minutos >

### Configurando acesso telnet 

>Router(config) # line vty < habilita telnet  em até 5 portas >
>
>Router(config-line) # login
>
>Router(config-line )# password < Insira a senha que desejar >
>
>Router(config-line) # login  < habilita a checagem da senha >
>
>Router(config-line) # exec-timeout 2  < Cadastrar time out para sessão telnet em 2 min>
>
>Router(config) # username < usuário > privilege 15 password < senha > < Criar usuário e senha para telnet >
>
>>*OBS.:Privilege 15 (valores de 0 a 15, 15 é full)*
>

### Configurando as interfaces 
> *Seriais e Ethernet*
>
> Router(config )# interface ethernet < número da porta > ou interface serial < número da porta >
>
>Router(config-if) # ip address < end > < masc >
>
>Router(config-if) # no shutdown < em todas as interfaces físicas para levantar a configuração >
>
>> *Descrição de interfaces (Serial ou Ethernet) - Visualizado pelo comando show*
>>
>> Router(config)# interface serial < número da porta >
>>
>> Router(config-if) # description ..... (até 256 caracteres)
>>
>>*Passive interface (interface passiva para atualização de roteamento)*
>>
>> Router(config-router)# passive-interface < número da porta >
>>
>> Router(config-router)# passive-interface < número da porta >
>

### Configurando o banner de inicialização
>
>Router(config) # banner Motd "msg que deseja"
>

### Configurando o  Http server
>>*Habilitar o acesso ao router via HTTP*
>
>Router(config) # ip http server
>

### Configurando o  DNS
>>*Habilitar DNS*
>
> Router(config)# ip domain-lookup
>
> Router(config)# ip name-server < end do server >
>
> Router(config)# ip domain-name local.< url do server>

### Configurar rotas estáticas
>
> Router(config) # ip route < ip destino > < máscara > < interface ou gw> < dist. admin>
>>
>>*Configurar rotas estáticas coringa*
>>
>>Router(config) # ip route 0.0.0.0 0.0.0.0 < end do próximo salto >

### Salvando configurações 
>
> Router # copy running-config startup-config < enter> ou do wr < enter> 
>

###  Setar data e hora no Router
>
> Router # clock set < h : m : s> < dia mês ano >

### Reinicializa o Router
>
> Router # reload

### Não deixa o dhcp resolver comandos errados
>
> berlim(config-line)# no transport preferred

### Comandos de verificação (SHOW)
>
>Router# show running-config /startup-config
>
>                 RAM    ------>  NVRAM
>
> Router# show interfaces F0/0 ou S0/0 ou S0/1 (no 2600) e E0 e S0 (no 1600)
>
> Router# show controllers (verificações físicas)
>
> Router# show ip route (mostrar as rotas e tipos de protocolos)
>
> Router# show ip protocols (verificar protocolos)
>
> Router# show running-config (ram)
>
>Router # show arp (Exibe a tabela ARP do roteador)