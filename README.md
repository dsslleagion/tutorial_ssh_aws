<!DOCTYPE html>
<html>
<head>

</head>
<body>

<h1>Tutorial de Configuração de Acesso Remoto com Chaves e Permissões de Usuário</h1>

<h2>Passo 1: Criar Usuários</h2>
<p>Primeiro, você deve criar os usuários usando o comando <code>adduser</code>. Por exemplo, para criar um usuário chamado "diretor", execute o seguinte comando:</p>

<pre><code>sudo adduser diretor</code></pre>

<p>Certifique-se de criar todos os usuários necessários desta maneira.</p>

<h2>Passo 2: Verificar Usuários Cadastrados</h2>
<p>Para verificar se todos os usuários estão cadastrados com êxito, faça login como o usuário "ubuntu" e navegue até a pasta home:</p>

<pre><code>cd /home
ls</code></pre>

<p>Você deve ver os diretórios dos usuários que você criou.</p>

![Imagem1](https://github.com/dsslleagion/tutorial_ssh_aws/assets/88494278/52c58fca-5a87-4566-b9de-f99cf940d976)


<h2>Passo 3: Configurar Chaves de Acesso</h2>
<p>Agora, vamos configurar chaves de acesso para os usuários "diretor", "suporte", "administrador", "vendedor" e "estagiario".</p>

<h3>3.1 Criar Diretório .ssh</h3>
<p>Para cada usuário, crie um diretório <code>.ssh</code> em sua pasta home:</p>

<pre><code>mkdir /home/nome_do_usuario/.ssh</code></pre>

<h3>3.2 Gerar Chave SSH</h3>
<p>Dentro do diretório <code>.ssh</code>, use o comando <code>ssh-keygen</code> para gerar uma chave SSH. Por exemplo:</p>

<pre><code>ssh-keygen</code></pre>

<p>Siga as instruções para gerar a chave. Dê um nome significativo à chave, como "diretorssh".</p>

<h3>3.3 Copiar Chave Pública para authorized_keys</h3>
<p>Agora, copie a chave pública para o arquivo <code>authorized_keys</code>:</p>

<pre><code>cat /home/nome_do_usuario/.ssh/nome_da_chave.pub >> /home/nome_do_usuario/.ssh/authorized_keys</code></pre>
<p>Ou</p>
<pre><code>cat diretorssh.pub > authorized_keys </code></pre>

<h3>3.4 Baixar Chaves com Bitvise</h3>
<p>Usando o cliente SSH Bitvise, baixe as chaves privadas correspondentes às chaves públicas geradas nos passos anteriores.</p>

![Imagem2](https://github.com/dsslleagion/tutorial_ssh_aws/assets/88494278/369e0f79-1689-4bc3-9660-3277477ec0c6)

<h2>Passo 4: Definir Permissões</h2>
<p>Para dar permissões aos usuários, você precisa editar o arquivo <code>sudoers</code>. Certifique-se de ter permissões de root para fazer isso. Use um editor de texto como <code>vim</code> ou <code>nano</code>. Por exemplo:</p>

<pre><code>sudo nano /etc/sudoers</code></pre>

<p>Adicione as configurações de permissões necessárias para os usuários.</p>

![Imagem3](https://github.com/dsslleagion/tutorial_ssh_aws/assets/88494278/091a0264-7227-4f27-aef5-e536a65090ac)

<h2>Passo 5: Negar Acesso Remoto de Usuários</h2>
<p>Se desejar negar o acesso remoto de um usuário específico, edite o arquivo <code>sshd_config</code>. Adicione o seguinte comando em uma linha, substituindo "nome do usuário" pelo nome do usuário que deseja negar o acesso:</p>

<pre><code>DenyUsers nome_do_usuário</code></pre>

![Imagem4](https://github.com/dsslleagion/tutorial_ssh_aws/assets/88494278/1e82daa0-531d-4d99-80e7-51a2d030c19c)

<p>Salve o arquivo e reinicie o serviço SSH para que as alterações tenham efeito.</p>



<p>Isso conclui o tutorial para configurar acesso remoto por chaves e gerenciar permissões de usuário em seu sistema Linux. Certifique-se de seguir as etapas com cuidado e tomar as medidas de segurança apropriadas.</p>

</body>
</html>
