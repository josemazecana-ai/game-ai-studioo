GAME AI STUDIO v3 — protótipo web 3D
- Editor de cena Three.js
- Gerar plano/descrição de jogo via OpenAI API (backend Express)
- Guardar projetos no localStorage do navegador
- Exportar projeto em JSON
- Adicionar casas, árvores, blocos e personagem

Setup:
1) Node.js 18+
2) npm install
3) copiar .env.example para .env
4) colocar OPENAI_API_KEY no .env (não publicar chave)
5) npm start
6) abrir http://localhost:3000

Deploy: host Node.js (Render/Railway/VPS), definir OPENAI_API_KEY nas env vars do serviço.
Aviso: geração de texto IA requer API e pode ter custo. A cena ainda é protótipo, não jogo AAA completo.
