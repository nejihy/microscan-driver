# driver do microscan

[![Status da construção](https://travis-ci.org/jonemo/microscan-driver.svg?branch=master)](https://travis-ci.org/jonemo/microscan-driver)
[![Versão PyPI](https://badge.fury.io/py/microscan.svg)](https://badge.fury.io/py/microscan)

Driver Python para leitores de código de barras Microscan

O autor deste software não é afiliado à Microscan Systems Inc.

"Microscan" e "MS3" são marcas comerciais da Microscan Systems Inc. e são usadas neste software e na documentação que o acompanha em benefício do proprietário da marca comercial, sem intenção de violação.


## Como instalar
​
Clone este repositório git ou baixe o repositório como um [pacote zip](https://github.com/jonemo/microscan-driver/archive/master.zip) e extraia.
Em seguida, na pasta raiz do repositório, execute

```
$ python setup.py instalação
```

Dependendo de sua configuração e ambiente,
você pode querer considerar fazer isso dentro de um [virtualenv](https://virtualenv.pypa.io/).
​
Este pacote possui apenas um único requisito (que é instalado automaticamente ao executar o comando acima):
A [biblioteca `pyserial`](https://pythonhosted.org/pyserial/) fornece acesso à porta serial e é implementada em Python puro.
Em outras palavras: Este driver não usa nenhuma extensão C e deve funcionar em muitas implementações Python.


## Como executar testes de unidade

Na pasta raiz do repositório, execute:

```
$ python -m unittest
```

Nenhuma dependência adicional é necessária.

## Dispositivos suportados

Atualmente, esta biblioteca visa implementar todos os recursos documentados no manual do usuário do dispositivo MS3 (com as exceções listadas abaixo).

​
## Recursos (ainda) não suportados
​
### Configurações específicas
​
As definições de configuração listadas abaixo não estão implementadas atualmente nesta biblioteca:

* Para a configuração do Host Port Protocol,
os valores "Multidrop", "Definido pelo usuário" e "Multidrop definido pelo usuário"
* Matchcode (todas as funcionalidades descritas no capítulo 7 do manual do usuário)
* Definições de configuração para as simbologias Codabar, Interleaved2Of5 e Pharmacode
​
Uma solução alternativa para aplicativos que exigem esses recursos,
é enviar as strings de configuração correspondentes diretamente usando o método `MicroscanDriver.write()`, por exemplo, para enviar apenas os dados do símbolo na correspondência, mas assim que os dados estiverem disponíveis:
​
```
driver = MicroscanDriver('COM3')

driver.write(b'<K705,1,0>')

driver.close()

```
​

### Funcionalidade geral
​
Nenhuma verificação de sanidade é executada nas combinações de configurações em uma configuração. Apenas as configurações individuais e suas subconfigurações são (em grau limitado) validadas em relação à especificação.
