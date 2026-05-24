# Atualizar imagens e assets do site

Este documento descreve como atualizar imagens e outros arquivos estáticos usados pela interface (`web/`).

Opções:

1) Desenvolvimento (sem instalar)
- Edite os arquivos em `web/imagens/` diretamente.
- Inicie o app com Python para testar: 

```powershell
py -3 PersonalMoldes.py
```

As mudanças aparecem imediatamente quando o app é executado a partir da pasta fonte.

2) Aplicação instalada (via `setup.exe`)
- Por padrão o instalador agora extrai a pasta `web/` para a pasta de instalação (por exemplo `C:\Program Files (x86)\PersonalMoldes\web`).
- Para atualizar as imagens em uma instalação existente você tem duas opções:
  - Manually replace the image files inside the installation folder (e.g. `C:\Program Files (x86)\PersonalMoldes\web\imagens\logo_header.png`).
  - Use the app built-in asset updater (see `ASSETS_UPDATE_URL` in `config.json`) to pull a zip with updated assets remotely.

3) Rebuild e novo instalador
- Se você quiser incluir mudanças dentro do executável (quando estiver usando `web` incorporado), siga os passos em `docs/RELEASE.md`.

---

# Configuração do atualizador

No `config.json` você pode adicionar:

```json
{
  "ASSETS_UPDATE_URL": "https://example.com/assets.zip",
  "AUTO_UPDATE_ASSETS": true
}
```

- `ASSETS_UPDATE_URL`: URL pública para um arquivo ZIP contendo a estrutura `web/` (por exemplo `web/imagens/*`).
- `AUTO_UPDATE_ASSETS`: quando `true`, o app tentará baixar e extrair os assets no primeiro startup.

Se preferir, mantenha `AUTO_UPDATE_ASSETS` desligado e chame manualmente a função de atualização (implementação já incluída em `PersonalMoldes.py`).
