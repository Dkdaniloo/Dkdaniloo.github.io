```markdown
# Aplicação de Gerenciamento Bancário

- Informar nome, sobrenome e CPF   
- Consultar saldo
- Realizar depósitos
- Realizar saques
- Encerrar o uso da aplicação

class ContaBancaria:
    def __init__(self, nome, sobrenome, cpf):
        self.nome = nome
        self.sobrenome = sobrenome
        self.cpf = cpf
        self.saldo = 0.0

    def consultar_saldo(self):
        return f"Saldo atual: R${self.saldo:.2f}"

    def depositar(self, valor):
        if valor > 0:
            self.saldo += valor
            return f"Depósito de R${valor:.2f} realizado com sucesso."
        return "Valor de depósito inválido."

    def sacar(self, valor):
        if 0 < valor <= self.saldo:
            self.saldo -= valor
            return f"Saque de R${valor:.2f} realizado com sucesso."
        return "Saldo insuficiente ou valor de saque inválido."

def main():
    nome = input("Informe seu nome: ")
    sobrenome = input("Informe seu sobrenome: ")
    cpf = input("Informe seu CPF: ")
    conta = ContaBancaria(nome, sobrenome, cpf)

    while True:
        print("\n1. Consultar Saldo\n2. Depositar\n3. Sacar\n4. Encerrar")
        opcao = input("Escolha uma opção: ")

        if opcao == '1':
            print(conta.consultar_saldo())
        elif opcao == '2':
            valor = float(input("Informe o valor para depósito: "))
            print(conta.depositar(valor))
        elif opcao == '3':
            valor = float(input("Informe o valor para saque: "))
            print(conta.sacar(valor))
        elif opcao == '4':
            print("Encerrando aplicação...")
            break
        else:
            print("Opção inválida. Tente novamente.")

if __name__ == "__main__":
    main()