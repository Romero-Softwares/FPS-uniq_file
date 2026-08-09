# Forest War – Tático

**Forest War – Tático** é um FPS 3D de sobrevivência em navegador, implementado em uma única página (`fps.html`). O jogo usa Three.js via CDN, portanto não há etapa de build nem dependências para instalar.

## Recursos

- Modos **Sobrevivência** e **Missão Tática**.
- Ondas de inimigos, pontuação, abates, vida, munição, minimapa e bússola.
- Arsenal com fuzil M4, pistola PT-92 e granadas.
- Objetivo de extração no modo tático.
- Multiplayer P2P para até quatro jogadores, com troca manual dos códigos de conexão.
- Controles adaptados para mouse/teclado e toque em dispositivos móveis.

## Como jogar

1. Abra o jogo em um navegador compatível com WebGL.
2. Escolha o modo na tela inicial e selecione **INICIAR**.
3. Clique na tela do jogo para capturar o mouse e começar a mirar.

| Ação | Controle |
| --- | --- |
| Mover | `W`, `A`, `S`, `D` |
| Mirar | Mouse |
| Atirar | Clique esquerdo |
| Zoom | Botão direito do mouse |
| Recarregar | `R` |
| Trocar arma | `Q` / `E` |
| Correr | `Shift` |
| Pular | `Espaço` |

## Testar localmente

Embora seja possível abrir o arquivo HTML diretamente, use um servidor local para reproduzir melhor o ambiente de publicação e evitar restrições do navegador.

```powershell
python -m http.server 8000
```

Com o terminal aberto, acesse [http://localhost:8000/fps.html](http://localhost:8000/fps.html). Para encerrar o servidor, pressione `Ctrl+C` no terminal.

### Checklist rápido

- A tela inicial aparece e o modo pode ser selecionado.
- O clique em **INICIAR** abre o cenário e o mouse controla a mira.
- Movimento, disparo, recarga e troca de arma funcionam.
- O HUD atualiza vida, munição, inimigos e pontuação.

> O jogo carrega Three.js de um CDN público; por isso, o navegador precisa de conexão com a internet na primeira execução (ou enquanto o cache não estiver disponível).

## Publicar no GitHub Pages

O workflow em `.github/workflows/deploy-pages.yml` transforma `fps.html` em `index.html` e publica o site automaticamente a cada push para a branch `main`.

1. Crie um repositório vazio no GitHub.
2. No diretório deste projeto, execute:

   ```powershell
   git init
   git add fps.html .github .gitignore README.md
   git commit -m "Configura GitHub Pages"
   git branch -M main
   git remote add origin https://github.com/SEU_USUARIO/SEU_REPOSITORIO.git
   git push -u origin main
   ```

3. No GitHub, abra **Settings > Pages**.
4. Em **Build and deployment**, escolha **GitHub Actions** como fonte de publicação.
5. Aguarde o workflow **Deploy GitHub Pages** finalizar na aba **Actions**.

A URL pública será exibida em **Settings > Pages** e nos detalhes da execução do workflow. O endereço normalmente segue o formato `https://SEU_USUARIO.github.io/SEU_REPOSITORIO/`.

### Atualizações posteriores

Após mudar o jogo, publique uma nova versão com:

```powershell
git add fps.html README.md
git commit -m "Atualiza Forest War"
git push
```

O GitHub Pages será atualizado automaticamente após a conclusão do workflow.
