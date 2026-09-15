# Reflexão sobre o conflito de merge

## O que causou o conflito

Thiago e Gustavo editaram a **mesma linha** do `README.md` ao mesmo tempo, cada um na sua cópia local, sem sincronizar antes:

1. Ambos partiram do mesmo commit (`2404670`).
2. Thiago alterou a primeira linha e deu `git push` — o repositório remoto avançou.
3. Gustavo, sem ter dado `git pull` antes, alterou a mesma linha na sua cópia (que ainda estava desatualizada) e tentou `git push`.
4. O push do Gustavo foi rejeitado (`! [rejected] ... fetch first`), porque o remoto já tinha um commit que ele não tinha localmente.
5. Ao rodar `git pull`, o Git tentou combinar as duas versões automaticamente, mas como as duas mudanças estavam na mesma linha, ele não conseguiu decidir sozinho qual manter — gerando o conflito, marcado no arquivo com `<<<<<<<`, `=======` e `>>>>>>>`.

## Como resolvemos

Abrimos o `README.md`, comparamos as duas versões dentro dos marcadores de conflito, decidimos manter uma versão combinando as duas ideias, apagamos os marcadores (`<<<<<<<`, `=======`, `>>>>>>>`) e o texto duplicado, depois rodamos `git add README.md` e `git commit` para finalizar o merge, e por fim `git push`.

## Como evitar esse tipo de conflito no futuro

- Sempre rodar `git pull` **antes** de começar a editar, para começar do estado mais atualizado do repositório.
- Comunicar à dupla/equipe quando for mexer em um arquivo compartilhado (ex: README), evitando que duas pessoas editem a mesma parte ao mesmo tempo.
- Dividir o trabalho em arquivos ou seções diferentes sempre que possível, reduzindo a chance de duas pessoas tocarem na mesma linha.
- Fazer commits e pushes pequenos e frequentes, em vez de acumular muitas mudanças antes de sincronizar.
