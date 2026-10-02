# 🔄 Processo de Desenvolvimento

Este documento registra as principais interações realizadas com o Lovable após o envio do mega prompt, apresentando a sequência de instruções utilizadas durante o desenvolvimento e os ajustes realizados na aplicação.

As interações estão apresentadas em ordem cronológica, permitindo acompanhar a evolução da aplicação a partir da implementação inicial.

---

## 1. Primeira interação — Implementação da Fase 1

Após o envio do mega prompt, o Lovable iniciou a implementação da aplicação de maneira incremental.

Como resultado da primeira interação, a **Fase 1 foi concluída e testada**, contemplando a estrutura inicial da aplicação e os recursos de autenticação e gerenciamento da conta.

Entre os recursos implementados estavam:

- Cadastro e login por e-mail e senha ou Google;
- Recuperação e redefinição de senha;
- Saída da conta;
- Área privada protegida;
- Menu de navegação com Dashboard, Meu Perfil, Vagas, Currículos e Configurações;
- Dashboard com indicadores e estado vazio;
- Estrutura do banco de dados para armazenar perfil, experiências, formação, cursos, competências, idiomas, projetos, vagas, análises e currículos;
- Isolamento dos dados, garantindo que cada usuário visualize apenas seus próprios dados.

O Lovable informou que as páginas de perfil, vagas e currículos seriam implementadas nas fases seguintes.

Durante essa primeira interação, também foi identificado que as demais fases ainda não haviam sido executadas.

Após revisar o mega prompt, foi descoberto que a forma como a execução incremental havia sido descrita permitia interpretar que as fases seriam executadas em diferentes interações.

A intenção original, entretanto, era que o desenvolvimento fosse incremental, mas que todas as fases fossem executadas sequencialmente dentro de uma única interação.

---

## 2. Segunda interação — Continuidade da implementação

Para esclarecer a forma de execução, foi enviada a seguinte instrução:

> Quero que você implemente todas as demais fases de uma vez, mas seguindo a ordem.
>
> Implemente a Fase 2, confira se está tudo certo, e se sim já comece a Fase 3 e assim por diante.

O objetivo foi deixar explícito que as fases restantes deveriam ser executadas sequencialmente, realizando uma verificação entre elas e continuando até a conclusão da implementação.

### Resultado

O Lovable informou que as **Fases 2, 3 e 4 foram implementadas nessa ordem** e que a aplicação compilava sem erros. Entretanto, os fluxos envolvendo Inteligência Artificial ainda não haviam sido testados no navegador.

As principais funcionalidades implementadas foram:

### Meu perfil

- Edição de dados pessoais e resumo;
- Sugestão de conteúdo utilizando IA, com salvamento somente após aprovação;
- Cadastro, edição e exclusão de experiências;
- Cadastro, edição e exclusão de formação;
- Cadastro, edição e exclusão de cursos;
- Cadastro, edição e exclusão de competências;
- Cadastro, edição e exclusão de idiomas;
- Cadastro, edição e exclusão de projetos.

### Nova candidatura

O fluxo foi estruturado em três etapas:

1. **Fonte de dados:** escolha entre utilizar o perfil salvo ou colar um currículo. Quando um currículo é colado, a IA interpreta o conteúdo, permitindo sua revisão e, opcionalmente, o salvamento das informações no perfil.
2. **Dados da vaga:** preenchimento das informações da vaga, com possibilidade de salvar como rascunho.
3. **Revisão:** conferência dos dados antes da solicitação da análise de compatibilidade.

O sistema também apresenta as alterações que serão realizadas antes de salvar informações extraídas do currículo. Em caso de conflito com informações já existentes, o usuário pode escolher qual informação manter, sem sobrescrever os dados sem aviso.

### Página da vaga

Foram implementados:

- Percentual de compatibilidade calculado de acordo com a fórmula definida na especificação;
- Separação dos requisitos em atendidos, parcialmente atendidos e não identificados;
- Sugestões de melhoria divididas em três grupos;
- Histórico de análises;
- Reanálise de compatibilidade;
- Alteração de status;
- Exclusão da candidatura.

### Currículos

A geração do currículo passou a partir da análise de compatibilidade. O usuário pode:

- Selecionar as seções que deseja incluir;
- Escolher o idioma;
- Editar o conteúdo gerado;
- Visualizar o currículo antes da exportação;
- Exportar o currículo em PDF;
- Consultar o histórico de currículos.

O PDF é gerado com texto real, permitindo sua leitura por sistemas de triagem.

Após essa interação, o fluxo principal da aplicação estava implementado e passou a ser possível realizar testes mais completos.

---

## 3. Terceira interação — Edição do currículo antes da exportação

Após a implementação das funcionalidades, foram realizados testes na aplicação.

Durante os testes, foi identificado que algumas informações apareciam repetidas no currículo gerado. Esse problema não foi tratado naquele momento, pois seria necessário buscar mais informações para entender sua causa.

A solicitação seguinte foi focada exclusivamente na possibilidade de editar o currículo antes da exportação:

> Já está ótimo obrigado. Fiz alguns testes. Eu reparei no currículo tem algumas informacoes que se repetem, quando é criado. Eu não quero resolver isso agora, vou buscar mais informações de o porque está acontecendo isso.
>
> Agora, eu queria poder arrumar o currículo antes de baixar. Ou seja, editar ele. Atualmente é possível editar os campos. Alguns aparecem para serem editados na tela de geração do currículos, mas não aparece todos os campos. Eu queria poder clicar no currículo onde eu quisesse e editar. Excluir uma linha, editar alguma informação, etc. quero poder editar antes de baixar, para que eu não tenha que abrir ele novamente em um editor de texto fora da aplicação. Pode implementar isso pra mim? Não mude mais nada além disso. Não mexa em nada que estiver relacionado com isso

### Resultado

Foi adicionada a possibilidade de editar diretamente o currículo na visualização antes de realizar o download.

A nova funcionalidade permite:

- Clicar diretamente sobre textos do currículo e editá-los;
- Editar nome, contato, resumo, competências, cargos, tópicos, projetos, formação, cursos e idiomas;
- Excluir linhas individualmente;
- Excluir uma seção inteira;
- Adicionar novos tópicos às experiências;
- Salvar as alterações antes de sair da página;
- Exportar o currículo em PDF após as alterações.

O Lovable também informou que, no celular, as ações de exclusão que dependem de passar o mouse não ficam disponíveis da mesma forma que no computador.

As informações repetidas identificadas anteriormente não foram alteradas, conforme solicitado.

Durante essa interação, o Lovable também informou que realizou uma atualização de segurança nas dependências da aplicação.

---

## 4. Quarta interação — Correção do download do currículo no celular

Durante novos testes, foi identificado um problema no download do currículo em dispositivos móveis. O botão de exportação não estava funcionando corretamente.

Foi então enviada a seguinte instrução:

> Eu não estou conseguindo baixar o currículo pelo celular. O botão não funciona. Pode verificar pra mim?

### Resultado

O Lovable informou que corrigiu o comportamento do botão de exportação em dispositivos móveis.

Segundo a análise realizada, o problema estava relacionado à forma como o download era iniciado. Em dispositivos móveis, determinados tipos de download podem ser bloqueados pelo navegador.

Como solução, o comportamento passou a ser adaptado para dispositivos móveis:

- Ao tocar em **Exportar PDF**, o sistema tenta abrir o menu de compartilhamento do aparelho;
- O arquivo pode ser salvo ou compartilhado por aplicativos como WhatsApp ou e-mail;
- Caso o menu de compartilhamento não esteja disponível, o PDF é aberto em uma nova aba, permitindo que o usuário salve o arquivo.

### Testes realizados

O Lovable informou que:

- No computador simulado, o download continuou funcionando normalmente;
- No celular simulado, o PDF foi aberto em uma nova aba;
- O menu de compartilhamento não pôde ser testado, pois a ferramenta utilizada para os testes não disponibilizava esse recurso;
- O ambiente de visualização do próprio Lovable poderia apresentar limitações para downloads em dispositivos móveis, sendo recomendado testar a aplicação publicada diretamente no navegador do celular.

---

## 📚 Considerações finais

O desenvolvimento foi realizado de forma iterativa, utilizando o Lovable para implementar as funcionalidades e, posteriormente, realizar ajustes a partir dos testes realizados na aplicação.

As interações apresentadas neste documento demonstram a evolução do projeto desde a implementação inicial até os ajustes realizados após a utilização prática da aplicação.

O processo também evidenciou a importância de revisar as instruções fornecidas ao agente, validar os resultados obtidos e utilizar os testes realizados na aplicação para identificar novas necessidades e direcionar as próximas alterações.