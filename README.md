msg = 'SISTEMA BANCARIO v1.0'
print('-' * 42)
print(f'{msg.center(42)}')
print('-' * 42)

# Definições da conta
saldo = 0
limite = 500
extrato = []  # Alteração: extrato deve ser uma lista para armazenar transações
numero_saques = 0
LIMITE_SAQUES = 3

# Programa
opc = 'Menu de Opções'
menu = f"""{('-' * 42)}
{opc.center(42)}

[D] Depositar
[S] Sacar
[E] Extrato
[Q] Sair

{('-' * 42)}
"""
while True: #Loop do sistema
    
    print(menu)
    
    opcao = input('Digite uma Opção: ').strip().upper()[0] #Converte tudo para maiúsculas e pega a primeira letra

    if opcao == 'D':
        valor = float(input('Digite o valor do depósito: R$'))

        if valor > 0:
            saldo += valor
            extrato.append(f'Depósito: R${valor:.2f}')
            print('Depósito realizado com sucesso!')
        
        else:
            print('Operação Falhou! O valor informado é inválido')

    elif opcao == 'S':
        valor = float(input('Informe o valor que deseja sacar: R$'))
        
        if valor <= saldo and valor <= limite and numero_saques < LIMITE_SAQUES:
            saldo -= valor
            novo_saldo = saldo
            extrato.append(f'Saque: R${valor:.2f}')
            numero_saques += 1
            print('Saque Realizado com Sucesso!')
        
        else:
            print('Operação falhou! Verifique seu saldo, limite ou número de saques.')
        
    elif opcao == 'E':
        if not extrato:
            print('Você não tem transações no momento.')
        else:
            print('Extrao:')
            for transacao in extrato:
                print(transacao)
            print(f'Saldo atual: R${novo_saldo:.2f}')

    elif opcao == 'Q':
        msgsaida = 'SISTEMA_FINALIZADO'
        print('Até logo...')
        print(f'{msgsaida.center(42)}')
        break
    
    else:
        print('Opção Inválida! Tente novamente.')