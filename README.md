# **POC-4-FETCH**

Este repositório contém um projeto simples que utiliza o método **fetch** em JavaScript para gerar um Pokémon aleatório a partir da [PokéAPI](https://pokeapi.co/). Ao clicar em um botão, o usuário recebe a imagem e o nome de um Pokémon aleatório.

### **Status do Projeto**

✅ **Projeto Concluído**

### **Pré-requisitos**

Antes de começar, você vai precisar ter instalado em sua máquina as seguintes ferramentas:
- [Git](https://git-scm.com/)
- Um navegador web para visualização

### **🎲 Rodando o Projeto**

```bash
# Clone este repositório
$ git clone <https://github.com/KauaAlencar/POC-4-FETCH>

# Acesse a pasta do projeto no terminal/cmd
$ cd POC-4-FETCH

# Abra o arquivo index.html no seu navegador
```

### **Estrutura do Projeto**

O projeto é composto por um arquivo HTML (`index.html`) que contém a estrutura do gerador de Pokémon. O layout é simples e é feito com HTML e CSS. O JavaScript é usado para fazer chamadas assíncronas à PokéAPI.

### **Conteúdo**

O projeto conta com as seguintes funcionalidades:
- Um botão que, ao ser clicado, gera um Pokémon aleatório.
- Exibição do nome e da imagem do Pokémon retornado pela API.

### **Descrição do Código**

1. **Estrutura HTML**

    A estrutura HTML é composta por um título, um botão e um contêiner para mostrar o Pokémon gerado.
    
2. **Estilo CSS**

    O CSS garante que o layout seja responsivo e visualmente agradável, com um design simples que destaca o Pokémon gerado.

3. **Lógica JavaScript**

    A lógica de geração do Pokémon utiliza o método `fetch` para obter dados da API. Quando o botão é clicado, um ID aleatório é gerado, e uma chamada é feita à API para buscar o Pokémon correspondente.

   ### **Funcionamento do Método `fetch`**

O projeto utiliza o método `fetch` para fazer requisições assíncronas à **PokéAPI** e obter dados de Pokémons aleatórios. A seguir, explicamos como o `fetch` é utilizado no código:

```javascript
document.getElementById('fetch-button').addEventListener('click', () => {
    const maxPokemon = 1010; 
    const randomId = Math.floor(Math.random() * maxPokemon) + 1;
    const apiUrl = `https://pokeapi.co/api/v2/pokemon/${randomId}`;

    fetch(apiUrl)
        .then(response => {
            if (!response.ok) {
                throw new Error('Network response was not ok');
            }
            return response.json(); // Converte a resposta para JSON
        })
        .then(data => {
            const pokemonNome = document.getElementById('nome-pokemon');
            const pokemonImagem = document.getElementById('imagem-pokemon');

            pokemonNome.textContent = `#${data.id} - ${data.name.charAt(0).toUpperCase() + data.name.slice(1)}`;
            pokemonImagem.src = data.sprites.front_default; 
            pokemonNome.style.display = 'block';
            pokemonImagem.style.display = 'block';
        })
        .catch(error => {
            console.error('Erro ao buscar Pokémon:', error);
        });
});
```

#### **Explicação do Uso do `fetch`:**

1. **Início da Requisição**:
   - Quando o botão é clicado, um ID aleatório de Pokémon é gerado (de 1 a 1010) e a URL da API é construída com esse ID.

2. **Requisição Assíncrona**:
   - O método `fetch(apiUrl)` é chamado, iniciando a requisição para a PokéAPI. O `fetch` retorna uma `Promise`, que permite manipular a resposta assim que ela estiver disponível.

3. **Manipulação da Resposta**:
   - Utilizando o método `.then()`, verificamos se a resposta é bem-sucedida através da propriedade `ok`. Se não for, um erro é lançado.
   - Se a resposta for válida, chamamos `response.json()` para converter os dados da resposta em formato JSON. Isso também retorna uma `Promise`, que é manipulada em um próximo `.then()`.

4. **Exibição dos Dados**:
   - No segundo `.then()`, os dados do Pokémon (nome e imagem) são extraídos e exibidos na página. O nome é formatado para incluir o ID e a primeira letra maiúscula.

5. **Tratamento de Erros**:
   - O método `.catch()` é usado para capturar e lidar com erros que podem ocorrer durante a requisição ou ao processar a resposta. Caso ocorra um erro, uma mensagem é exibida no console.

Esse fluxo assíncrono permite que a aplicação permaneça responsiva, pois o navegador não fica bloqueado enquanto espera pela resposta da API.


### **Colaboradores**
<table>
  <tr>
    <td align="center"><a href="https://github.com/KauaAlencar"><img style="border-radius: 50%;" src="https://avatars.githubusercontent.com/u/172075258?v=4" width="100px;" alt=""/><br /><sub><b>Kauã Alencar</b></sub></a><br /><a href="https://www.linkedin.com/in/kau%C3%A3-alencar-b15119215/" title="Linkedin">🚀</a></td>
    <td align="center"><a href="https://github.com/GuilhermeShinohara"><img style="border-radius: 50%;" src="https://avatars.githubusercontent.com/u/180458966?v=4" width="100px;" alt=""/><br /><sub><b>Guilherme Shinohara</b></sub></a><br /><a href="https://github.com/GuilhermeShinohara" title="GitHub">🚀</a></td>
    <td align="center"><a href="https://github.com/LeoFavaron"><img style="border-radius: 50%;" src="https://avatars.githubusercontent.com/u/179886009?v=4" width="100px;" alt=""/><br /><sub><b>Leonardo Favaron</b></sub></a><br /><a href="https://github.com/LeoFavaron" title="GitHub">🚀</a></td>
  </tr>
</table>

### **📝 Licença**

Este projeto está sob a licença MIT.
