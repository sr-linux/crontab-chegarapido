# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command


#####################################################################
############ crons chegarapido delivery #############################
#####################################################################
# o complemento de comando " & echo" mostra na tela se a cron foi
# executada com sucesso...


# check estabelecimentos abertos a cada 5 min
*/5 8-23 * * * curl https://chegarapido.com.br/cron/checar-estabes-aberto-fechado.php & echo 'Cron check estabelecimentos' = ok >> ~/cron.log

# check seguranca 3 da manha
0 3  * * * curl https://chegarapido.com.br/cron/seguranca.php & echo 'Cron check seguranca = ok' >> ~/cron.log

# check taxas de entregas a cada 5 min
*/5 8-23 * * * curl https://chegarapido.com.br/cron/taxas-entregas.php & echo 'Cron check taxas entregas = ok' >> ~/cron.log

# check usuarios dias sem comprar 2x ao dia
0 0,12 * * * curl https://chegarapido.com.br/cron/usuarios-dias-sem-comprar.php & echo 'Cron check usuarios dias sem comprar = ok' >> ~/cron.log

# check pagseguro a cada 1 minuto
*/1 8-23 * * * curl https://chegarapido.com.br/cron/pagseguro.php & echo 'Cron check pagseguro = ok' >> ~/cron.log

# check limpar fechamentos a cada 1 minuto
*/1 8-23 * * * curl https://chegarapido.com.br/cron/limpar-fechamentos-chec.php & echo 'Cron check limpar fechamentos = ok' >> ~/cron.log

# limpar fechamentos as 7:45
45 7 * * * curl https://chegarapido.com.br/cron/limpar-fechamentos.php & echo 'Cron limpar fechamentos as 7:45 = ok' >> ~/cron.log

# check extrato entregador a cada 5 min
*/5 8-23 * * * curl https://chegarapido.com.br/cron/extrato-entregador.php & echo 'Cron check extrato entregador = ok' >> ~/cron.log

# limpar ips duplicados a cada 15 min
*/15 8-23 * * * curl https://chegarapido.com.br/cron/limpar-ips-duplicados.php & echo 'Cron limpar ips duplicados = ok' >> ~/cron.log

# bloquear entregadores sem  ponto de 2 em 2 horas
0 2 * * * curl https://chegarapido.com.br/cron/bloquear-entregadores-sem-ponto.php & echo 'Cron bloquear entregadores sem ponto = ok' >> ~/cron.log

# add id cidade 30 em 30 min
0,30 8-23 * * * curl https://chegarapido.com.br/cron/cron/add-id-cidade.php & echo 'Cron add id cidade = ok' >> ~/cron.log

# emails lidos a meia noite uuuhl
* 0 * * * curl https://chegarapido.com.br/cron/email-total-de-lidos.php & echo 'Cron emails lidos a meia noite = ok' >> ~/cron.log

# relatorio total estabelecimentos de 30 em 30 min
*/30 8-23 * * *  curl https://chegarapido.com.br/cron/relatorio-totalizador-estabelecimentos.php & echo 'Cron relatorio total de estabelecimentos = ok' >> ~/cron.log

# email marketing para nao clientes toda segunda meia noite
* 0 * * 1 curl https://chegarapido.com.br/cron/envio-email-marketing-para-pessoas-que-nunca-comprou.php & echo 'Cron email marketing para nao clientes = ok' >> ~/cron.log

# email marketing para pessoas com muito tempo sem comprar terca meia noite
* 0 * * 2 curl https://chegarapido.com.br/cron/cron/envio-email-marketing-para-pessoas-muito-tempo-sem-comprar.php & echo 'Cron email marketing pessoas muito tempo sem comprar = ok' >> ~/cron.log

# push alert pedido a aprovar estabelecimento de 1 em 1 min
*/1 8-23 * * * curl https://chegarapido.com.br/cron/push-alert-pedido-a-aprovar-para-estabelecimento.php & echo 'Cron push alert pedido aprovar estabelecimento = ok' >> ~/cron.log

# check pagamento mercado pago e pix de 1 em 1 min
*/1 8-23 * * * curl https://chegarapido.com.br/cron/checa-pagamento-mercado-pago-pix.php & echo 'Cron check pagamento mercado pago pix = ok' >> ~/cron.log

# check pedidos extornados todos os dias 23:30
30 23 * * * curl https://chegarapido.com.br/cron/estornar-cashbacks-de-pedidos-extornados.php & echo 'Cron check pedidos extornados = ok' >> ~/cron.log

# email marketing aniversariantes todos os dias a meia noite
* 0 * * *  curl https://chegarapido.com.br/cron/envio-email-marketing-para-pessoas-aniversariantes.php & echo 'Cron email marketing aniversariantes = ok' >> ~/cron.log

# email marketing geral todos os dias a meia noite
* 0 * * * curl https://chegarapido.com.br/cron/envio-email-marketing.php & echo 'Cron email marketing geral = ok' >> ~/cron.log

# check dashboard todo dia
0 */6 * * *  curl https://chegarapido.com.br/cron/dashboard.php & echo 'Cron check dashboard = ok' >> ~/cron.log

# aniversariantes do dia as 6 da manha

* 6 * * * curl https://chegarapido.com.br/cron/cupons-aniversariantes-do-dia.php & echo 'Cron cupons aniversariantes = ok' >> ~/cron.log

# expira cupons a cada hora

0 * * * * curl https://chegarapido.com.br/cron/cupons-expira.php & echo 'Cron cupons aniversariantes = ok' >> ~/cron.log
