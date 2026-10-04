# ブリキ戦車

Three.js のブラウザ向け見下ろし型戦車アクション（『はじめてのWii』の「タンク！」風）。claude.ai の Artifact として公開している。

- 公開先: https://claude.ai/artifact/18HJ7MZHTXWWNaN51WMmHA
- `game/index.html` — ゲーム一式（1ファイル）。更新はこのファイルを同じ URL へ再公開する。
- ローカル確認: `.claude/launch.json` の `tank`（Blender 同梱 Python の http.server、port 8766）
- テスト用フック: コンソールの `__tank.step(秒)` でタブが裏にあってもゲームを進められる。`__tank.goto(n)` でステージ n+1 へ、`__tank.aimAt(x,z)` で照準。

## 構成（index.html 内）
- `STAGES` — 22×15 の ASCII マップ（`.` 床 / `#` ブロック / `H` 2段ブロック / `c` コルク / `o` 穴 / `P` 自機 / `1-9` 敵種）
- `TYPES` — 敵 9 種のパラメータ（速度・弾数・弾速・跳弾回数・地雷・照準方式・回避率など）
- AI: `simulateShot` で跳弾を含む射線を探索、`threatFor` で回避、BFS で移動先を決める
- 効果音と BGM はすべて WebAudio で合成（`AU`, `MUSIC`）
