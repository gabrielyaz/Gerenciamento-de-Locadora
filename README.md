# Gerenciamento de Filmes em uma Locadora

## Descrição do Projeto
Este sistema é uma aplicação desenvolvida em Java, projetada para o Gerenciamento de um Catálogo de Filmes em uma Locadora. Organizado em pacotes para garantir a modularização e facilitar a manutenção do código, o sistema oferece funcionalidades como aluguel, devolução e gerenciamento de filmes. Além disso, conta com recursos adicionais, como o controle de status de aluguel e uma aba de login. O sistema suporta dois tipos de usuários: Usuário comum e Administrador, proporcionando diferentes níveis de acesso. É uma solução ideal para pequenas empresas.

## Estrutura do Projeto

# Pacotes 
O projeto está segmentado em três pacotes principais:

**Locadora**: Sua principal função é gerenciar os filmes disponíveis na locadora, permitindo que usuários comuns aluguem e devolvam filmes. Já as funcionalidades dos administradores incluem o gerenciamento do catálogo e o controle de operações restritas.
**Dados**: Este pacote armazena os atributos de cada filme no catálogo da locadora.
**Login**: Responsável pelo cadastro e autenticação de usuários, garantindo a verificação da existência de um usuário e o controle de permissões. Somente administradores têm acesso a informações restritas.
## Classes
- Pacote Dados:
    - Classe Filmes: Responsável por definir os filmes disponíveis na Locadora
    **Atributos**:
    - codigo (int): Código único de identificação do filme
    - nomeFilme (String): Nome do filme
    - diretor (String): Nome do diretor
    - estudio (String): Nome do estúdio
    - anoLancamento (int): Ano de lançamento
    - categoria (char): Categoria do filme
    - alugado (boolean): Indica se o filme está alugado (true) ou não (false)

    **Métodos**:
    - toString(): Gera uma saída em String simples dos atributos (Público-alvo: Sistema)
    - toTesxt(): Gera uma saída mais descritiva e intuitiva (Público-alvo: Usuário)

  - Getters:  
    - getNomeFilme(): Retorna o nome do filme
    - getDiretor(): Retorna o nome do diretor
    - getAnoLnacamento(): Retorna o ano do lancamento
    - isAlugado(): Retorna em boolean a disponibilidade do filme

  - Setters:
    - setNomeFilme(String nomeFilme): Atualiza o nome do filme
    - setCategoria(char categoria): Atualiza a categoria do filme
    - setAlugado(boolean alugado): Atualiza o status do aluguel do filme

    **Construtor**: Define os atributos do filme com os novos valores recebidos

- Pacote Locadora:
    - Classe Locadora: Contém a lista de filmes e métodos responsáveis por interagir com os filmes
    **Atributos**:
    - filmes (ArrayList<Filmes>): Lista de filmes cadastrados

    **Métodos**:
    - save(): Salva o catálogo de filmes em um arquivo txt (saves.txt)
    - load(): Carrega os filmes do arquivo saves.txt
    - mostrarFilmes(): Exibe todos os filmes do catálogo
    - procurarFilme(): Procura e exibe um filme a partir do nome
    - alugarFilme(): Aluga um filme, se disponível
    - devolverFilme(): Marca um filme como devolvido

    - Classe Adm: Contém métodos específicos para a aba de Administrador
    - addFilme(): Adiciona um novo filme ao catálogo
    - removerFilme(): Exclui um filme do catálogo

- Pacote Login:
    - Classe Dados: Responsável pela autenticação de usuários, dados pessoais e autorização de administrador
    **Atributos**:
    - usuario (String): Nome do usuário
    - senha (String): Senha do usuário
    - cpf (String): CPF do usuário
    - ADM (boolean): Verifica se o usuário é Administrador

    **Métodos**:
    - toString(): Representa os dados do usuário como uma String simples, para consulta do arquivo/sistema
  - Getters:
    - getUsuario(): Retorna o nome do usuário
    - getSenha(): Retorna a senha do usuário
    - getCpf(): Retorna CPF do usuário
    - isADM(): Retorna com true or false se o usuário é Adm

  - Setters: 
    - setUsuario (String usuario): Atualiza o nome de usuário
    - setSenha (String senha): Atualiza a senha do usuário

    **Construtor**: Define os atributos de usuário e senha com os novos valores recebidos

    - Classe Login: Responsável por gerenciar os usuários, permite cadastro, login e autenticação
    **Atributos**:
    - dados (ArrayList<Dados>): Armazena usuários cadastrados

    **Métodos**:
    - addUsuario(): Adiciona um novo usuário à lista de dados
    - load(): Carrega os usuários do arquivo "dadosUsuarios.txt"
    - verificarUsuario(): Verifica se o usuário está cadastrado no sistema
    - save(): Salva os dados dos usuários no arquivo "dadosUsuarios.txt"
    - mostrarUsuarios(): Exibe todos os usuários cadastrados no sistema

- Classe Sistema (main): Localizada na raiz do projeto, responsável por administrar a navegação do sistema entre Adm e Usuário. Exibe o menu.
    **Métodos**:
    - sistemAdm(): Define o comportamento do sistema quando reconhece um Usuário Administrador
    - sistemUsuario(): Define o comportamento do sistema quando reconhece um Usuário comum

- Classe Main: Controla a execução principal do programa

## Arquivo
- saves.txt: Armazena os dados dos filmes, garantindo a persistência do catálogo durante o as execuções do programa
- dadosUsuarios.txt: Armazena os dados  dos usuários

## Tratamento de Erros
- Erro ao carregar dados: No método load(), se houver problemas ao ler os arquivos de usuários ou filmes (ex. IOException), o código usa try-catch e lança uma RuntimeException, interrompendo a execução com uma mensagem de erro.

- Erro ao salvar dados: No método save(), ao tentar escrever no arquivo, se ocorrer um erro (ex. falta de permissão), o código usa try-catch e lança uma RuntimeException para interromper a execução e mostrar a falha.

- Entrada inválida: Ao capturar a opção do usuário (ex. nextInt()), o código usa try-catch para verificar se a entrada é válida. Se for inválida, uma mensagem de erro é exibida e o usuário é solicitado a tentar novamente.

- Dados inválidos no cadastro: No método verificarUsuario(), se as credenciais forem incorretas, o sistema não permite o login e exibe uma mensagem de erro.

- Filme não encontrado: No método mostrarFilmes(), se o filme não existir ou a lista estiver vazia, o código captura o erro e exibe uma mensagem informando que o filme não foi encontrado.

- Erro ao alugar ou devolver filme: Nos métodos alugarFilme() e devolverFilme(), se o filme não existir ou não estiver disponível, uma exceção é capturada e uma mensagem de erro é exibida.

- Erro ao remover filme: No método removerFilme(), se o filme não existir no catálogo, o código verifica e, em caso de erro, exibe uma mensagem informando que não foi possível remover o filme.

## Fluxo do Programa
- Inicialização do programa: O programa começa com a execução da classe Main
- Menu: Após a inicialização, o programa exibe a aba de Menu, com as seguintes opções:
    *[1] Já possui cadastro?(Fazer login)*
    *[2] Não possui cadastro? (Cadastrar)*
    *[3] Verificar usuários cadastrados*
    *[5] Sair do sistema*

- Opção 1: Já possui cadatro?
    Se o usuário escolher a opção 1, o sistema solicitará seu nome de usuário e senha; se as informações forem válidas: 
    SE Adm, então interface Administrativa.
    SE Usuário comum, então unterface de Usuário comum.

    Se as informações de login não forem válidas, o sistema informa que o usuário não foi encontrado

- Opção 2: Não possui cadastro?
    Se o usuário escolher a opção 2, o sistema solicitará seu nome de usuário, senha, se é Adm ou não, e seu CPF.
    A partir dessas informações, o sistema cria um novo usuário. 

- Opção 3: Verificar usuários cadastrados
    Se o usuário escolher a opção 3, o sistema exibirá todos os usuários cadastrados

- Opção 5: Sair do sistema
    Se o usuário escolher a opção 5, o programa é finalizado

*Menu do Usuário*
    - 1: Alugar um filme.
    - 2: Devolver um filme.
    - 3: Exibir todos os filmes do catálogo.
    - 4: Procurar um filme específico
    - 5: Deslogar do sistema

*Menu do Administrador*
    Caso o usuário seja um Adm, o menu administrativo será aberto, com as seguintes opções:
    - 1: Adicionar um novo filme ao catálogo.
    - 2: Remover um filme do catálogo.
    - 3: Alugar um filme.
    - 4: Devolver um livro:
    - 5: Exibir todos os filmes do catálogo.
    - 6: Procurar um filme específico.
    - 7: Sair so sistema>
Fim do Programa.


Através deste documento, esperamos ter fornecido uma visão clara e acessível do funcionamento do sistema, suas funcionalidades principais e como ele pode ser estendido ou melhorado no futuro. Se você tiver sugestões, dúvidas ou encontrar alguma área que possa ser otimizada, sinta-se à vontade para contribuir ou entrar em contato. 

