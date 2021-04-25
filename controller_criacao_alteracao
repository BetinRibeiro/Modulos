
@auth.requires_login()
def cadastrar():
#cria tela generica
  response.view = 'generic.html' # use a generic view
  #modifica o nome da função
  request.function='Renomear a função'
  #busca empresa pelo id passado pelo argumento
  empresa = db.empresa(request.args(0, cast=int))
  #define valor padrão 
  db.classe.empresa.default=empresa.id
  #renderiza formulario
  form = SQLFORM(db.classe).process()
  #quando formulario aceito
  if form.accepted:
      response.flash = 'Formulario aceito'
      #essa opção abaixo é que não esquecer como funciona quando precisamos de informções
      #que vem como retorno no formulario que já foi validado
      #db.cliente_vendedor.insert(cliente=form.vars.id,cpfCnpj=form.vars.cpfCnpj)
      #redireciona para outr pagina
      redirect(URL('index'))
  elif form.errors:
      response.flash = 'Formulario não aceito'
  else:
      response.flash = 'Preencha o formulario'
  return  dict(form=form)
  
  
  
#alterar e cadastrar pode estar dentro de outra estrutura
@auth.requires_login()
def alterar():
  response.view = 'generic.html' # use a generic view
  request.function='Renomear a função'
  form = SQLFORM(db.classe, request.args(0, cast=int), deletable=False)
  if form.process().accepted:
      session.flash = 'Dados atualizado'
      redirect(URL('index')
  elif form.errors:
      response.flash = 'Erros no formulário!'
  return dict(form=form)
