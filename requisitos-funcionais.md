# Requisitos Funcionais

- **USU01 - Cadastro:** O usuário poderá se cadastrar no sistema. O sistema deve permitir que o usuário entre com os seus dados pessoais.

- **USU02 - Alteração de dados pessoais:** O sistema deve permitir que o usuário possa alterar seus dados pessoais.

- **USU03 - Alteração de senha:** O sistema deve permirtir que o usuário possa fazer a alteração de sua senha.

- **USU04 - Autenticação:** O sistema deve permitir que os usuário possam realizar login a partir de suas credenciais, e-mail e senha. Após o processo de autenticação ser realizado com sucesso o sistema deve disponibilizar um token de acesso.

- **USU05 - Reautenticação:** O sistema deve permitir que os usuário obtenham um novo token de acesso sem a necessidade do usuário enviar novamente suas credenciais. Usuário irá enviar o seu token de reautenticação atual e então o sistema irá gerar um novo token de acesso.

- **CON01 - Cadastrar conta:** O usuário poderá cadastrar novas contas, no momento do cadastro o usuário proverá as informações da conta e então o sistema irá realizar o seu cadastro e então associar a conta cadastrada ao usuário que fez o seu cadastro.

- **CON02 - Listar contas:** O usuário poderá listar todas as suas contas já cadastradas, por padrão as contas devem ser ordenadas pela data de cadastro da mais recente para a mais antiga.

- **CON03 - Detalhes da conta:** O usuário poderá visualizar os detalhes de uma conta.

- **CON04 - Alterar dados da conta:** O usuário poderá alterar os dados de uma conta.

- **CON05 - Excluir conta:** O usuário poderá excluir uma conta. Caso a conta possua alguma transação, as transação associadas a esta conta também devem ser apagadas.

- **CON06 - Calcular saldo:** O usuário poderá verificar o saldo de uma conta. O sistema deve realizar este calculo com base em todas as transações associadas com a conta em questão.

- **CON07 - Listar transações da conta:** O usuário poderá listar todas as transações associadas com a conta em questão;

- **TRA01 - Cadastrar transação:** O usuário poderá cadastrar uma nova transação, no momento do cadastro o usuário deverá informar para qual conta a transação será associada e qual o tipo da mesma, se é uma transação de entrada ou de saida.

- **TRA02 - Listar transações:** O usuário poderá listar todas as transações que o mesmo cadastrou.

- **TRA03 - Detalhes da transação:** O usuário poderá exibir os detalhes de uma transação.

- **TRA04 - Alterar dados da transação:** O usuário poderá alterar todos os dados de uma transação.

- **TRA05 - Excluir transação:** O usuário poderá excluir uma transação.