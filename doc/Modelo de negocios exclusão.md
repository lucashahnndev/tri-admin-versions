# Modelo de Negócios de Exclusão

Este documento descreve o modelo de negócios de exclusão adotado pelo software. O modelo tem como objetivo permitir que os usuários possam excluir objetos manipulados pelo sistema ou objetos cadastrados pelos usuários e possam restaurá-los posteriormente, se necessário.
atraves do modelo de negócios de exclusão implementado no software, os usuários podem excluir objetos com a possibilidade de restaurá-los posteriormente. Esse processo é feito por meio da marcação da data de exclusão na coluna "trash_date" da tabela correspondente ao objeto. Além disso, há um gerenciador de lixeira que verifica periodicamente a data de exclusão dos objetos e os exclui permanentemente após 30 dias. Isso possibilita que o usuário possa reciclar um objeto excluído sem querer ou excluí-lo permanentemente. Os objetos excluídos não interagem mais com o sistema, exceto na lixeira e registros. Eles também não estão disponíveis na pilha de sincronização ou contagem de objetos. O modelo de negócios de exclusão permite que os agentes capacitados possam restaurar objetos excluídos por acidente ou mudança de ideia.

## Sumário

- [Introdução](#introdução)
- [Resumo](#resumo)
- [Exclusão de Objetos Manipulados pelo Sistema](#exclusão-de-objetos-manipulados-pelo-sistema)
- [Exclusão de Objetos Manipulados pelos Usuários](#exclusão-de-objetos-manipulados-pelos-usuários)
- [Recuperação de Objetos Excluídos](#recuperação-de-objetos-excluídos)
- [Objetos Excluídos e sua Interatividade com o Sistema](#objetos-excluídos-e-sua-interatividade-com-o-sistema)
- [Objetos Disponíveis na Lixeira](#objetos-disponíveis-na-lixeira)
- [Objetos Disponíveis para Visualização](#objetos-disponíveis-para-visualização)
- [Sincronização de Exclusão de Objetos](#sincronização-de-exclusão-de-objetos)
- [Restauração de Objetos Excluídos](#restauração-de-objetos-excluídos)
- [Conclusão](#conclusão)

## Introdução

A exclusão de objetos em um software é um processo comum e importante para manter o banco de dados organizado e atualizado. No entanto, pode acontecer de um objeto ser excluído por engano ou o usuário mudar de ideia e desejar restaurá-lo posteriormente. Para solucionar esse problema, o modelo de negócios de exclusão implementado no software permite que o usuário possa excluir e restaurar objetos.

Este documento descreve o modelo de negócios de exclusão adotado pelo software. O modelo tem como objetivo permitir que os usuários possam excluir objetos manipulados pelo sistema ou objetos cadastrados pelos usuários e possam restaurá-los posteriormente, se necessário.

## Resumo

O modelo de negócios de exclusão implementado no software permite que os usuários possam excluir objetos com a possibilidade de restaurá-los posteriormente. Esse processo é feito por meio da marcação da data de exclusão na coluna "trash_date" da tabela correspondente ao objeto. Além disso, há um gerenciador de lixeira que verifica periodicamente a data de exclusão dos objetos e os exclui permanentemente após 30 dias. Isso possibilita que o usuário possa reciclar um objeto excluído sem querer ou excluí-lo permanentemente. Os objetos excluídos não interagem mais com o sistema, exceto na lixeira e registros. Eles também não estão disponíveis na pilha de sincronização ou contagem de objetos. O modelo de negócios de exclusão permite que os agentes capacitados possam restaurar objetos excluídos por acidente ou mudança de ideia.

## Exclusão de Objetos Manipulados pelo Sistema

Os objetos manipulados pelo sistema são excluídos permanentemente e imediatamente após serem marcados como excluídos.

## Exclusão de Objetos Manipulados pelos Usuários

Todos os objetos e cadastros que são manipulados pelos usuários possuem uma coluna na sua tabela nomeada como "trash_date". Quando o usuário marca o objeto como excluído, a coluna do respectivo objeto é marcada com a data atual da exclusão.

Após a marcação de exclusão, existe um gerenciador de lixeira que verifica em todas as tabelas que são manipuladas pelos usuários. Se algum objeto possuir uma data na coluna "trash_date" e esta data tiver 30 dias ou mais, na hora da verificação o gerenciador de lixeira irá excluí-lo permanentemente.

## Recuperação de Objetos Excluídos

Este modelo de negócios possibilita que o usuário recupere algum cadastro que ele tenha excluído sem querer, ou excluí-lo permanentemente. Para isso, o agente terá de visitar a lixeira e escolher uma das duas opções.

## Objetos Excluídos e sua Interatividade com o Sistema

Apesar de um objeto não ser excluído imediatamente, ele não estará disponível nas listagens de objetos, e o sistema não permitirá que ele seja visualizado (apenas na lixeira e registros). Esse objeto não estará na pilha de sincronização (nem a dos softwares ou a de softwares de terceiros integrados ao sistema) apenas na lista de exclusão, e também não fará parte das contagens de objetos.

## Objetos Disponíveis na Lixeira

Objetos que tiverem algum valor em "trash_date" (isto quer dizer que a coluna "trash_date" do objeto não tem o valor "null") estarão disponíveis somente na aba lixeira do objeto e no registro de logs para o departamento com permissão de manipular aquele objeto.

## Objetos Disponíveis para Visualização

Também estarão disponíveis nos relatórios de agentes para o agente que tiver permissão de visualizar aquele item, se ele estiver no seu escopo de ALTERAÇÃO. Se o usuário estiver em um departamento que não tem permissão alguma sobre aquele objeto mas possa ver os registros, no log ele somente poderá ver o nome e ID do objeto excluído.

## Sincronização de Exclusão de Objetos

Os objetos marcados como excluídos entrarão na lista de sincronismo de exclusão de softwares de terceiros que estiverem integrados imediatamente.

## Restauração de Objetos Excluídos

Caso alguns dos agentes pertencentes ao departamento capacitado de manipular aquele item excluído opte por restaurar o objeto, assim que o objeto for marcado como restaurado a coluna "trash_date" é marcada como nula ("null") e volta a interagir imediatamente com o sistema

## Conclusão

Em resumo, o modelo de negócios de exclusão implementado no software permite que os usuários possam excluir objetos com a possibilidade de restaurá-los posteriormente. Esse processo é feito por meio da marcação da data de exclusão na coluna "trash_date" da tabela correspondente ao objeto. Além disso, há um gerenciador de lixeira que verifica periodicamente a data de exclusão dos objetos e os exclui permanentemente após 30 dias.
