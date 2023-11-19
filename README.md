from prettytable import PrettyTable
import mysql.connector


conexao = mysql.connector.connect(
    host="localhost",
    user="root",
    password="302302",
    database="academia_turma_d"
)


cursor = conexao.cursor()
print(conexao)
print("")
print (f"=-=-=-="*5,"CRUD","=-=-=-="*5)
print("")
print("")
print("selecione o numero que voce quer : ")
print("")
tabelas = int(input("digite: 1-Alunos / 2-Funcionarioa / 3-Matriculado / 4-Modalidades / 5-Personal"))
rep = 1

#CRUD
while True:
    if rep == 1:
        while True:
            if tabelas > 1:
                print("Escolha a tabela que você deseja :  ")
                print("")
                print("")
              
                print("")
                tabelas = int(input("digite: 1-Alunos / 2-Funcionarioa / 3-Matriculado / 4-Modalidades / 5-Personal"))
                print("")
                
            else:
                campos = int(input("digite: 1- inserir / 2- Deleta / 3-Ler / 4-SAIR"))
                if campos == 4:
                    break

                while True:
                    if campos > 4:
                        print("")
                        print("Nao existe essa opção")
                        print("")
                        campos = int(input("digite: 1- inserir / 2- Deleta / 3-Ler / 4-SAIR "))
                        if campos == 4:
                            break
                        

                    elif campos == 1:
                        print("")
                        print("opção de inserir")
                        print("")
                        nome = input("digite seu nome : ")
                        print("")
                        email = input("digite seu email : ")
                        print("")
                        cpf = input("Digite seu CPF: ")
                        print("")
                        comando = f'insert into alunos(nome,email,cpf) values ("{nome}","{email}","{cpf}")' 
                        cursor.execute(comando)
                        conexao.commit()
                        rep = int(input("quer repetir ? \n\n 1-Sim / 2-Nao"))
                        if rep == 2:
                            break
                            

                    elif campos == 2:
                        print("Você escolheu excluir")
                        print("")
                        x = int(input("digite o ID do aluno que voce quer excluir : "))
                        comando = f'delete from alunos where ID_alunos = {x} '
                        cursor.execute(comando)
                        conexao.commit()
                        print("apagado com sucesso")
                        rep = int(input("quer repetir ? \n\n 1-Sim / 2-Nao"))
                        if rep == 2:
                            break     
