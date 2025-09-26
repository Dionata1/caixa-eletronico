# caixaeletronico.py

saldo = 1000.00  # saldo inicial
limite_saque = 3
saques_realizados = 0
extrato = []

def exibir_menu():
    print("\n=== Caixa Eletrônico ===")
    print("1. Ver saldo")
    print("2. Sacar")
    print("3. Depositar")
    print("4. Ver extrato")
    print("5. Sair")

def ver_saldo():
    print(f"\nSeu saldo atual é: R$ {saldo:.2f}")

def sacar():
    global saldo, saques_realizados
    if saques_realizados >= limite_saque:
        print("\n⚠️ Limite de saques diários atingido.")
        return
    try:
        valor = float(input("Informe o valor para saque: R$ "))
        if valor <= 0:
            print("⚠️ Valor inválido.")
        elif valor > saldo:
            print("⚠️ Saldo insuficiente.")
        else:
            saldo -= valor
            saques_realizados += 1
            extrato.append(f"Saque: -R$ {valor:.2f}")
            print(f"✅ Saque de R$ {valor:.2f} realizado com sucesso.")
    except ValueError:
        print("⚠️ Entrada inválida. Digite um número.")

def depositar():
    global saldo
    try:
        valor = float(input("Informe o valor para depósito: R$ "))
        if valor <= 0:
            print("⚠️ Valor inválido.")
        else:
            saldo += valor
            extrato.append(f"Depósito: +R$ {valor:.2f}")
            print(f"✅ Depósito de R$ {valor:.2f} realizado com sucesso.")
    except ValueError:
        print("⚠️ Entrada inválida. Digite um número.")

def ver_extrato():
    print("\n=== Extrato ===")
    if not extrato:
        print("Nenhuma movimentação realizada.")
    else:
        for item in extrato:
            print(item)
    print(f"Saldo atual: R$ {saldo:.2f}")

# Loop principal
while True:
    exibir_menu()
    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        ver_saldo()
    elif opcao == "2":
        sacar()
    elif opcao == "3":
        depositar()
    elif opcao == "4":
        ver_extrato()
    elif opcao == "5":
        print("Saindo... Obrigado por usar o caixa eletrônico!")
        break
    else:
        print("⚠️ Opção inválida. Tente novamente.")
