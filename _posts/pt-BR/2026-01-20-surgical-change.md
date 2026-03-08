---
title: Mudança Cirúrgica
date: 2026-01-20
lang: pt-BR
categories: [engineering, tech, process]
tags: [softskill, process]
---

# Uma pequena mudança

Existem situações em que uma mudança pequena, aparentemente inofensiva, pode ter um impacto desproporcional na vida de muitas pessoas.

Quando nós, como desenvolvedores, começamos a construir sistemas que ajudam no diagnóstico de problemas de saúde, controlam a injeção de medicamentos no corpo de alguém ou gerenciam o voo de 300 pessoas, as consequências das nossas mudanças importam. Não enxergamos sempre o impacto das nossas alterações... Aquele pequeno refactor que você fez pode potencialmente introduzir um bug que afete drasticamente a vida de alguém. Dê uma olhada [Lista de erros de sistemas que mataram pessoas](https://en.wikipedia.org/wiki/List_of_software_bugs).

No dia a dia do trabalho, muitas vezes não percebemos além de um arquivo que não segue convenções de nomenclatura ou classes fortemente acopladas. A beleza — ou feiura — do código torna-se nossa prioridade máxima. Gastamos tanto tempo decidindo nomes e estrutura que perdemos algo muito importante: o processo de engenharia.
Para quem estou fazendo isso — para mim, para o cliente da empresa ou para a empresa?

A maioria de nós não trabalha em sistemas críticos para a vida. Ainda assim, é importante ter clareza sobre quem será afetado pelo código que escrevemos. Qual é o valor de refatorar um sistema legado se ele quebrar no processo?

# Refatoração

Não sou contra refatoração; todo desenvolvedor deve refatorar regularmente. Código que não evolui fica obsoleto até que alguém queira reescrever tudo porque nada funciona. O problema real, porém, não é o estado do sistema, e sim as pessoas responsáveis por ele: desenvolvedores, gerentes e stakeholders. Eles falharam em manter o pulso do sistema saudável.
Refatoração é o pulso de um sistema. Se você refatora todo dia ou somente uma vez por ano, ambos os extremos estão errados. Refatores frequentes e desesperados sinalizam um sistema em parada cardíaca; revisões anuais significam que o sistema está, na prática, morto.

Seja claro: melhore o sistema um pouco a cada dia. Pequenas mudanças — melhorar nomes, remover código desnecessário, refatorar um switch para um padrão Factory ou Strategy — podem ser feitas junto com o trabalho em features ou correção de bugs. Não há necessidade de avisar o PM ou seu gerente para mudanças pequenas. Se uma refatoração leva dias ou semanas, não é refatoração — é uma reescrita. Algumas partes do sistema podem ter sido tão mal construídas que exigem uma mudança quase completa para funcionar ou para se tornarem compreensíveis.

Mudanças em um sistema devem entregar valor, inclusive refatores. Tenha cuidado para não quebrar algo que já funciona. Na minha opinião, refatores exigem mais cautela do que a adição de novas features.

O valor precisa ser o motivo por trás de uma refatoração: melhorar legibilidade, documentação, separar responsabilidades, etc. Mas nenhum desses motivos deve nascer do ego ou do “divertimento”. Programadores às vezes refatoram “só por diversão”. É satisfatório transformar código confuso em algo bonito, mas prazer não pode ser o único motivo. Mudanças precisam de contexto e propósito.

# Processo de Engenharia

Ao alterar software, reflita sempre sobre o "porquê". Quem se beneficia? Como você medirá o sucesso? Como saberá que o sistema melhorou?

Comece com um objetivo claro e uma forma de medi-lo. Para valores subjetivos como legibilidade, busque a opinião de outros desenvolvedores para que a mudança possa ser avaliada.

Trate isso como refinamento: descreva o que melhorar, como isso afetará o sistema e como os testes devem ser escritos. Testes são críticos pois revelam sistemas relacionados e pontos de integração.
Em seguida, conte ao seu gerente ou stakeholder sobre a refatoração planejada. Explique detalhes, prós e contras. Pense no que pode dar errado. Busque críticas de alguém que vá desafiar suas ideias e ajudar a melhorá-las. Revisões aumentam o valor de uma mudança e podem revelar quando ela não tem valor.

Esse processo — documentar a mudança, planejar, pedir revisão e iterar — é um loop de feedback usado por muitas metodologias ágeis e de design. Não pule a etapa de escrever a especificação da mudança: um caso de uso, uma user story, uma tarefa, a descrição de uma feature ou um relatório de bug. Escrever o que precisa mudar e por quê é um **processo necessário**.

Enquanto documenta, você descobrirá falhas no seu raciocínio e no código que não havia previsto. Isso ajuda a estimar o tamanho e o impacto da mudança e fornece evidências para convencer seu gerente de que a refatoração vale a pena.

# Mudança Cirúrgica

>
> "That is, instead of each member cutting away on the problem, one does the cutting and the others give him every support that will enhance his effectiveness and productivity. "
>
> Brooks Jr., Frederick P.. The Mythical Man-Month: Essays on Software Engineering (p. 47).

Durante o refinamento, procuro uma mudança cirúrgica: a modificação que entrega mais valor com o menor impacto no comportamento do sistema. Mais fácil falar do que fazer, eu sei, mas esse é o objetivo.

Meu processo para identificar essa mudança geralmente começa depois que elimino todas as dúvidas sobre o negócio. Primeiro faço perguntas de esclarecimento ao product manager e então examino o código.
Ao inspecionar o código sigo quatro passos:

- **Identificar o ponto de partida da mudança** — onde a alteração deve começar; qual arquivo fonte é a entrada de implementação.
- **Identificar dependências** — anotar sistemas relacionados, façades, bibliotecas e dependências internas ou externas que serão afetadas.
- **Fazer um rascunho** — experimentar para ver o que quebra. Isso não é implementação completa; é testar para descobrir problemas. Se algo quebrar, simule ou stubbeie e prossiga. Quais sistemas falham? Quais testes precisam ser atualizados?
- **Escrever testes que validem a ideia** — criar testes que capturem o bug, a feature ou o objetivo da refatoração. Eles vão falhar no início; isso é esperado.

Os dois últimos passos podem ser mesclados em um fluxo de trabalho de Test‑Driven Development. Essas etapas são diretrizes — não seja escravo de nenhuma metodologia; aplique o que funciona melhor no seu contexto.

Engenharia de software não é uma tarefa fácil. Desenvolvedores escrevem código e documentação todo dia; ambos exigem atenção para evitar erros que podem causar bugs graves. Um processo repetível — uma forma confiável de trabalhar — ajuda a prevenir esquecimentos e constrói hábitos produtivos.

References: 

[Expecting professionalism](https://www.youtube.com/watch?v=HD0L3lQ9cms&pp=ugMICgJwdBABGAHKBQ51bmNsZSBib2IgdGFsaw%3D%3D)