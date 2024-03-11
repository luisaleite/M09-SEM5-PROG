# M09-SEM5-PROG

# Questão
A partir da documentação oficial do Cypress, prepare um documento de texto contendo as seguintes informações:

1. O que é o Cypress e para que serve?
2. Vantagens e desvantagens do Cypress em relação a outras ferramentas de teste.
3. Arquitetura do Cypress.
4. Seletores de elementos no Cypress.
5. Comandos e asserções no Cypress.
6. Descrição das etapas de preparação de um testes de interface, execução e verificação no Cypress.
7. Como estruturar testes de forma eficiente no Cypress?

O documento deve ser entregue em markdown em um repositório do github.

Não se esqueça de tornar o repositório público ou atribuir acesso aos professores.

Link adicional: https://docs.cypress.io/guides/overview/why-cypress


# 1. O que é o Cypress e para que serve?

O Cypress é um framework open-source que simplifica a configuração de testes automatizados, para testes de ponta a ponta (E2E). Ele não requer a instalação de várias ferramentas e bibliotecas separadas, tornando a configuração mais rápida e fácil. Além disso, o Cypress é escrito em JavaScript e utiliza o Node.js como servidor e interpretador, o que facilita a integração com projetos de desenvolvimento web modernos.

O Cypress é muito comparado com o Selenium mas existe uma grande diferença entre eles primeiro que o Selenium opera fora do navegador e executa comandos remotamente, já o Cypress executa testes no mesmo ciclo de execução do sistema em teste isso acaba tornando o processo mais rápido

Sua funcionalidade é automatizar testes de software, principalmente para aplicações web.  Ele simula ações de usuários como preencher formulários, clicar em botões e navegar por páginas, ajudando a garantir que o software funcione como esperado.

# 2. Vantagens e desvantagens do Cypress em relação a outras ferramentas de teste.

**Suas vantagens são:**

- Facilidade no uso: por conta de sua documentação objetiva e interface intuitiva, a curva de aprendizado é considera relativamente suave
- Execução rápida: ele é executado diretamente no navegador, o que torna os testes muito mais rápidos na execução.
- Feedback em tempo real: O Cypress fornece feedback em tempo real sobre os resultados dos testes, o que facilita a depuração de problemas.
- Versatilidade: O Cypress pode ser usado para testar diferentes tipos de aplicações web, incluindo aplicações de página única (SPA).
- Captura de Vídeo e Screenshots: A capacidade de capturar vídeos e screenshots durante a execução dos testes é uma característica valiosa do Cypress. Essas mídias são úteis para análise pós-teste e para compartilhar resultados com a equipe.

**Suas desvantagens são:**

- Apenas para aplicações Web: O Cypress é projetado especificamente para testes em aplicações web, o que pode ser limitante para projetos que incluem diferentes tipos de aplicativos, como mobile ou desktop.
- Suporte ao navegador: Cypress oferece compatibilidade ****apenas com Firefox e navegadores baseados em Chromium, como o Google Chrome e o Microsoft Edge. O Cypress tem suporte experimental para o WebKit, o motor de navegador usado pelo Safari. O Cypress não suporta o Edge legado ou o Internet Explorer.
- Assíncrono Limitado: Embora o Cypress execute testes de maneira síncrona, pode haver desafios com operações assíncronas complexas. Isso pode exigir o uso de comandos específicos para contornar essas situações.
- Não Suporta Requisições Cross-Domain: O Cypress tem restrições quanto a fazer solicitações entre domínios diferentes. Embora existam soluções para contornar isso, pode ser uma barreira para projetos que dependem fortemente de interações cross-domain.

| Diferença em termos de | Cipreste | Selênio |
| --- | --- | --- |
| velocidade de execução | Usa a execução no navegador para enviar comandos por meio de eventos DOM, resultando em comandos síncronos na memória e testes rápidos. | Utiliza comunicação fora do processo para enviar comandos via WebDriver, resultando em comunicação assíncrona e testes mais lentos. |
| Estrutura de teste | Restrito ao framework de teste Mocha e não pode usar outros frameworks JavaScript como Jest ou Tape. | Nenhuma aplicação da estrutura de teste e pode usar qualquer estrutura JavaScript ou até mesmo programas que não sejam de teste. |
| Modelo de Execução | Grava comandos como cy.clique or tipo.cy para ser reproduzido mais tarde após o término da função. | Executa comandos diretamente, permitindo a execução de código com base no valor da página. |
| Mocking de Servidor Integrado | Possui funções integradas para zombar das respostas do servidor, permitindo testes rápidos. | Não possui funções integradas para simular as respostas do servidor e requer a execução de um servidor simulado, resultando em testes mais lentos. |

# 3. Arquitetura do Cypress.

A arquitetura do Cypress se direfe das outras por conta de executar no mesmo ciclo de execução da aplicação, ou seja, se trata de uma abordagem in-processo. Os pontos de arquitetura do Cypress são:

- **Servidor Node.js:** O Cypress é executado por um processo servidor Node.js rodando em background.
- **Comunicação constante:** O Cypress e o processo Node.js se comunicam constantemente para executar tarefas e sincronizar ações.
- **Acesso amplo:** Essa arquitetura dá ao Cypress acesso a ambos os lados (front-end e back-end) da sua aplicação, permitindo que ele responda a eventos da aplicação em tempo real.
- **Controle de Rede:** O Cypress também opera na camada de rede, podendo ler e alterar o tráfego da web em tempo real. Isso permite que ele não apenas modifique dados que entram e saem do navegador, mas também altere códigos que interfiram na automação.
- **Controle centralizado:** Ao controlar todo o processo de automação, o Cypress obtém uma visão completa do que acontece dentro e fora do navegador, resultando em testes mais consistentes.

# 4. Seletores de elementos no Cypress.

O Cypress oferece uma variedade de seletores de elementos que serve para localizar e iteragir com elementos específicos na página que esta em teste. Estes seletores permitem que você realize ações como clicar em botões, preencher formulários e verificar o conteúdo de elementos.

Os tipos de seletores são esses:

1. Seletor por ID: cy.get('#id')
2. Seletor por classe: cy.get('.class')
3. Seletor por tag: cy.get('element')
4. Seletor por atributo com valor específico: cy.get('[attribute=value]')
5. Seletor por atributo que contém um valor específico: cy.get('[attribute*=value]')
6. Seletor por atributo que começa com um valor específico: cy.get('[attribute^=value]')
7. Seletor por atributo que termina com um valor específico: cy.get('[attribute$=value]')
8. Seletor pelo n-ésimo elemento filho: cy.get(':nth-child(n)')
9. Seletor pelo n-ésimo elemento do tipo específico: cy.get(':nth-of-type(n)')
10. Seletor para o primeiro elemento filho: cy.get(':first-child')
11. Seletor para o último elemento filho: cy.get(':last-child')
12. Seletor para todos os elementos exceto os selecionados: cy.get(':not(selector)')
13. Seletor para elementos de input que estão marcados: cy.get(':checked')
14. Seletor para elementos desabilitados: cy.get(':disabled')
15. Seletor para elementos habilitados: cy.get(':enabled')
16. Seletor para o elemento que está atualmente em foco: cy.get(':focus')
17. Seletor para o elemento quando o cursor do mouse está sobre ele: cy.get(':hover')
18. Seletor para elementos sem filhos: cy.get(':empty')
19. Seletor para elementos que são filhos únicos: cy.get(':only-child')
20. Seletor para elementos que são o único do seu tipo entre os irmãos: cy.get(':only-of-type')
21. Seletor para o elemento raiz <html>: cy.get(':root')
22. Seletor para o elemento alvo de um hyperlink: cy.get(':target')
23. Seletor para links visitados: cy.get(':visited')
24. Seletor para o primeiro conteúdo filho de um elemento, inserido antes do conteúdo principal: cy.get('::before')
25. Seletor para o último conteúdo filho de um elemento, inserido após o conteúdo principal: cy.get('::after')
26. Seletor para a primeira letra de um elemento de bloco: cy.get(':first-letter')
27. Seletor para a primeira linha de um elemento de bloco: cy.get(':first-line')
28. Seletor para o texto selecionado: cy.get('::selection')
29. Seletor por atributo que contém um valor específico dentro de uma lista, separado por espaços: cy.get('[attribute~="value"]')
30. Seletor para o n-ésimo elemento filho, contando do último para o primeiro: cy.get(':nth-last-child(n)')
31. Seletor para o n-ésimo elemento do tipo específico, contando do último para o primeiro: cy.get(':nth-last-of-type(n)')
32. Seletor para o último elemento do tipo específico: cy.get(':last-of-type')
33. Seletor para todos os elementos que não correspondem ao seletor especificado: cy.get(':not(selector)')
34. Seletor para elementos com o atributo lang correspondendo ao idioma especificado: cy.get(':lang(language)')
35. Seletor por atributo com valor específico, ignorando a diferenciação entre maiúsculas e minúsculas: cy.get('[attribute="value" i]')
36. Seletor para elementos que contêm o texto especificado: cy.contains('text')
37. Seletor para elementos que têm um subelemento que corresponde ao seletor especificado: cy.get(':has(selector)')
38. Seletor para elementos que correspondem a um dos seletores especificados: cy.get(':matches(selector)')
39. Seletor para a coluna n-ésima em uma tabela: Não há um seletor direto, mas pode ser alcançado por meio da estrutura da tabela.
40. Seletor para a coluna n-ésima, contando da última para a primeira em uma tabela: Similar ao anterior, não há um seletor direto para isso.
41. Seletor para o primeiro elemento do tipo específico: cy.get(':first-of-type')
42. Seletor para elementos que são filhos únicos: cy.get(':only-child')
43. Seletor para elementos cujo placeholder está visível: Não há um seletor direto, mas você pode verificar a visibilidade do placeholder usando um seletor mais amplo.
44. Seletor para elementos somente leitura: cy.get(':read-only')
45. Seletor para elementos editáveis: cy.get(':read-write')
46. Seletor para elementos com atributo required: cy.get(':required')
47. Seletor para elementos inválidos: cy.get(':invalid')
48. Seletor para elementos válidos: cy.get(':valid')
49. Seletor para elementos com estado indeterminado: cy.get(':indeterminate')
50. Seletor para elementos opcionais: cy.get(':optional')

# 5. Comandos e asserções no Cypress.

Asserções são um tipo de consulta exibida especialmente no log de comando

**Os Comandos e Asserções no Cypress são esses:**

- cy.get() - Encontra elementos no DOM usando vários seletores.
- cy.visit() - Visita uma URL específica.
- cy.click() - Clica em um elemento.
- cy.type() - Digita texto em um campo de entrada.
- cy.clear() - Apaga o conteúdo de um campo de entrada.
- cy.contains() - Verifica se um elemento contém um texto específico.
- cy.wait() - Aguarda um período de tempo específico.
- cy.reload() - Recarrega a página atual.
- cy.go() - Navega para frente ou para trás no histórico do navegador.
- cy.debug() - Abre o debugger do Cypress.
- cy.should() - Verifica se um elemento possui uma propriedade específica.
- cy.expect() - Usa a biblioteca Chai para realizar asserções mais complexas.
- cy.eq() - Verifica se dois elementos são iguais.
- cy.not() - Verifica se um elemento não possui uma propriedade específica.
- cy.be.visible() - Verifica se um elemento está visível.
- cy.be.hidden() - Verifica se um elemento está oculto.
- cy.have.text() - Verifica se um elemento contém um texto específico.
- cy.have.class() - Verifica se um elemento possui uma classe específica.
- cy.have.attr() - Verifica se um elemento possui um atributo específico.

# 6. Descrição das etapas de preparação de um testes de interface, execução e verificação no Cypress.

**Preparação:**

1. Abra o seu terminal.
2. Navegue até o diretório do seu projeto.
3. Execute o comando npm init para inicializar um novo projeto npm.
4. Em seguida, execute o comando npm install cypress –save-dev para instalar o Cypress como uma dependência de desenvolvimento em seu projeto.
5. Aguarde até que a instalação seja concluída.

**Execução:**

1. Abra o seu terminal de preferência.
2. Navegue até o diretório do seu projeto.
3. Execute o comando npx cypress open para abrir a interface do Cypress.
4. Selecione o arquivo de teste que deseja executar na interface do Cypress.
5. Aguarde até que o Cypress execute os testes e exiba os resultados.

**Verificação:**

Ao final da execução dos testes, o Cypress irá exibir um relatório detalhado dos resultados. Você poderá verificar quais testes passaram, quais falharam e obter informações adicionais sobre as falhas, como mensagens de erro e screenshots.

# 7. Como estruturar testes de forma eficiente no Cypress?

**1. Organize seus testes em pastas e arquivos.**

Crie pastas para organizar seus testes de acordo com a funcionalidade que eles testam. Por exemplo, você pode ter pastas para "Login", "Registro", "Perfil do Usuário", etc.

Dentro de cada pasta, você pode criar arquivos para testes específicos. Por exemplo, na pasta "Login", você pode ter arquivos para "Login com sucesso", "Login com falha", "Esqueci minha senha", etc.

**2. Use comandos descritivos.**

Use comandos descritivos para facilitar a leitura do seu código. Por exemplo, em vez de usar `cy.get('input')`, use `cy.get('input[name="username"]')`.

**3. Use asserções para verificar se o seu código está funcionando como esperado.**

As asserções são usadas para verificar se o resultado de um teste é o esperado. Por exemplo, você pode usar a asserção `cy.contains('Olá, usuário!')` para verificar se a página contém o texto "Olá, usuário!".

**4. Use o debugger do Cypress para solucionar problemas.**

O debugger do Cypress é uma ferramenta poderosa que pode te ajudar a solucionar problemas nos seus testes.

**5. Crie funções e módulos para reutilizar código.**

Se você estiver repetindo o mesmo código em vários testes, você pode criar funções ou módulos para reutilizar esse código.

**6. Integre o Cypress com ferramentas de CI/CD.**

Você pode integrar o Cypress com ferramentas de CI/CD para executar testes automaticamente após cada alteração no código.

# Fonte
1. https://www.linkedin.com/pulse/diferen%C3%A7as-entre-selenium-e-cypress-anderson-mann/?originalSubdomain=pt
2. https://awari.com.br/aprenda-a-utilizar-o-cypress-para-testes-de-frontend/?utm_source=blog&utm_campaign=projeto+blog&utm_medium=Aprenda%20A%20Utilizar%20O%20Cypress%20Para%20Testes%20De%20Frontend
3. https://docs.cypress.io/guides/getting-started/opening-the-app
4. https://medium.com/stonetech/10-boas-pr%C3%A1ticas-essenciais-para-o-seu-dia-a-dia-com-o-cypress-7f6e8d87e55
5. https://medium.com/@thiago-castilho/introdu%C3%A7%C3%A3o-ao-cypress-um-guia-passo-a-passo-para-testes-de-aplica%C3%A7%C3%B5es-web-6be295b0557
