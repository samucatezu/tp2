# validacao-CPF-Vuejs


- A página deverá receber no mínimo três informações:
**Nome,
RA e
CPF do usuário**

- A tela deverá ter uma área para exibição da mensagem de retorno da função ao lado do campo de inserção de CPF
- Um arquivo .js deverá ser criado com uma função que recebe o CPF como parâmetro e retorna as msg "CPF Válido" ou "CPF inválido"
- A função deverá calcular os dígitos do CPF usando o algoritmo disponível no link https://www.macoratti.net/alg_cpf.htm

- A função deverá comparar com os dois dígitos informados
- Se não for informado um CPF, deverá exibir a msg "Informe um CPF" na área da tela descrita no item 2 desta atividade
- Se o CPF informado tiver tamanho menor que 11, deverá exibir a msg "CPF incompleto" na área da tela descrita no item 2 desta atividade
- Se o CPF informado contiver caracteres não numéricos, deverá exibir a msg "CPF com caracteres inválido" na área da tela descrita no item 2 desta atividade
- Se os dígitos informados forem diferentes dos dígitos calculados, deverá exibir a msg "CPF inválido" na área da tela descrita no item 2 desta atividade
- Se forem iguais, deverá exibir a mensagem "CPF Válido" na área da tela descrita no item 2 desta atividade.


## Screenshots

![Screenshot](https://github.com/samucatezu/validacao-CPF-Vuejs/blob/master/public/img/CPF_Incompleto.png)
![Screenshot](https://github.com/samucatezu/validacao-CPF-Vuejs/blob/master/public/img/CPF_Informe.png)
![Screenshot](https://github.com/samucatezu/validacao-CPF-Vuejs/blob/master/public/img/CPF_Valido.png)
![Screenshot](https://github.com/samucatezu/validacao-CPF-Vuejs/blob/master/public/img/Forms_informe.png)




## Rodando localmente

Clone o projeto

```bash
  git clone https://github.com/samucatezu/validacao-CPF-Vuejs
```

Entre no diretório do projeto

```bash
  cd my-project
```

Instale as dependências

```bash
  yarn install
```

Inicie o servidor

```bash
  yarn serve
```
