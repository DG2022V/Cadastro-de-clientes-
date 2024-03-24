# Cadastro-de-clientes-
Este código cria uma classe Cliente com atributos para nome, email e telefone, e métodos para exibir as informações do cliente.

from flask import Flask, render_template, request, jsonify

app = Flask(__name__)

clientes = []

@app.route('/')
def index():
    return render_template('index.html')

@app.route('/cadastrar_cliente', methods=['POST'])
def cadastrar_cliente():
    cliente = {
        'nome': request.form['nome'],
        'email': request.form['email'],
        'telefone': request.form['telefone']
    }
    clientes.append(cliente)
    return jsonify({'mensagem': 'Cliente cadastrado com sucesso!'})

@app.route('/clientes')
def listar_clientes():
    return jsonify(clientes)

if __name__ == '__main__':
    app.run(debug=True)
