4-2 
<img width="1405" height="885" alt="image" src="https://github.com/user-attachments/assets/e2b2a741-71f4-4bba-a1a3-547239ddf295" />
Me gera uma senha aleatoria sem sentido ou padrão
<img width="1301" height="602" alt="image" src="https://github.com/user-attachments/assets/3904221d-a224-4622-ab44-91fcc883e180" />
import secrets
import string

def gerar_senha_segura(tamanho=12):
    if tamanho < 4:
        raise ValueError("A senha deve ter pelo menos 4 caracteres.")

    # Conjuntos de caracteres
    letras_maiusculas = string.ascii_uppercase
    letras_minusculas = string.ascii_lowercase
    numeros = string.digits
    especiais = string.punctuation

    # Garante pelo menos um de cada tipo obrigatório
    senha = [
        secrets.choice(letras_maiusculas),
        secrets.choice(letras_minusculas),
        secrets.choice(numeros),
        secrets.choice(especiais)
    ]

    # Preenche o restante da senha
    todos_caracteres = letras_maiusculas + letras_minusculas + numeros + especiais
    senha += [secrets.choice(todos_caracteres) for _ in range(tamanho - 4)]

    # Embaralha a senha para não ficar previsível
    secrets.SystemRandom().shuffle(senha)

    return ''.join(senha)


# Exemplo de uso
if __name__ == "__main__":
    print(gerar_senha_segura(16))

