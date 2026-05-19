# EV ChargeGrid EcoCore

## Integrantes
### João Victor Canello Ferian-rm573295
### Gustavo Melo dos Santos-rm573562
### João pedro costenari silva-rm572260

## Problema
A ineficiência computacional em eletropostos.

## Justificativa
Com o crescimento da mobilidade elétrica, torna-se necessário desenvolver soluções mais eficientes também no nível computacional. Mesmo utilizando energia limpa, muitos eletropostos ainda desperdiçam energia durante o processamento interno devido ao uso de sistemas pouco otimizados. O objetivo do projeto é tornar os eletropostos mais eficientes utilizando metodos mais sustentaveis

## Solução
Sistema embarcado otimizado em Assembly.

## Arquitetura Utilizada
- RISC-V RV32I
- Pipeline.

## Código Exemplo
### Exemplo simples em RISC-V para monitoramento de sensor:
    LW x1, 0(x2)
    ADDI x3, x0, 80
    BLT x1, x3, OK
    J ALERTA

    OK:
    ADD x4, x1, x0

    ALERTA:
    SUB x5, x1, x3

### Sistema de Autenticacao em RISC-V, Arquitetura RV32I
    .data
    usuario_correto: .asciz "admin"
    senha_correta:   .asciz "1234"

    msgUser: .asciz "Usuario: "
    msgPass: .asciz "Senha: "
    msgOK:   .asciz "Acesso permitido!\n"
    msgErro: .asciz "Acesso negado!\n"

    usuario: .space 20
    senha:   .space 20

    .text
    .globl main

    main:

#### Exibe "Usuario:"
    la a0, msgUser
    li a7, 4
    ecall

#### Le usuario
    la a0, usuario
    li a1, 20
    li a7, 8
    ecall

#### Exibe "Senha:"
    la a0, msgPass
    li a7, 4
    ecall

#### Le senha
    la a0, senha
    li a1, 20
    li a7, 8
    ecall

#### Compara usuario
    la t0, usuario
    la t1, usuario_correto
    li t2, 5

comparar_usuario:

    lb t3, 0(t0)
    lb t4, 0(t1)

    bne t3, t4, acesso_negado

    addi t0, t0, 1
    addi t1, t1, 1
    addi t2, t2, -1

    bnez t2, comparar_usuario

#### Compara senha
    la t0, senha
    la t1, senha_correta
    li t2, 4

comparar_senha:

    lb t3, 0(t0)
    lb t4, 0(t1)

    bne t3, t4, acesso_negado

    addi t0, t0, 1
    addi t1, t1, 1
    addi t2, t2, -1

    bnez t2, comparar_senha

#### Acesso permitido
acesso_permitido:

    la a0, msgOK
    li a7, 4
    ecall

    j fim

#### Acesso negado
acesso_negado:

    la a0, msgErro
    li a7, 4
    ecall

#### Encerrar programa
fim:

    li a7, 10
    ecall

##### Impactos Esperados
- Menor custo operacional
- Menor uso de energia
- Melhor desempenho

## Sustentabilidade
Sistemas de carregamento, normalmente, utilizam computadores e aplicações que executam muitas instruções desnecessárias, aumentando os gastos e desperdícios, o uso de tecnologias mais eficientes contribui para uma mobilidade elétrica mais sustentável, eficiente e tecnologicamente otimizada.
