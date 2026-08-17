# PortfolioDev

Portfólio pessoal full-stack com galeria de mídia e sistema de feedback, com foco
em explorar armazenamento de arquivos binários no MongoDB (GridFS) e streaming de
vídeo via HTTP Range requests.

## Destaques técnicos

- **Streaming de vídeo com suporte a HTTP Range** — implementação manual de
  respostas `206 Partial Content` em chunks, permitindo que o navegador faça
  seek no vídeo sem baixar o arquivo inteiro.
- **Armazenamento binário via GridFS** — imagens e vídeos são guardados
  diretamente no MongoDB, usando o driver nativo com buckets dedicados.
- **Feedback persistido via Mongoose**, com schema próprio.

## Tecnologias

- Node.js + Express
- MongoDB — Mongoose (feedback) e driver nativo + GridFS (mídia binária)
- Multer (upload em memória)
- HTML/JS vanilla + Bootstrap 5 + SCSS no frontend
- Docker, com deploy realizado no Google Cloud Run *(atualmente fora do ar)*

## Endpoints principais

- `POST /feedback` — envio de feedback
- `POST /upload`, `GET /files`, `PUT /files/index/:index`, `DELETE /files/index/:index` — gestão de imagens
- `POST /upload/video`, `GET /videos`, `PUT /videos/index/:index`, `DELETE /videos/index/:index` — gestão de vídeos, com streaming via Range requests

## Como rodar localmente

\`\`\`bash
npm install
\`\`\`

Crie um arquivo `.env` na raiz do Backend com:
\`\`\`
MONGODB_URI=<sua_string_de_conexão>
DB_NAME=<nome_do_banco>
PORT=<porta>
\`\`\`

\`\`\`bash
npm start
\`\`\`

## Limitações conhecidas

Este foi um projeto de estudo focado em explorar as tecnologias acima — algumas
lacunas conscientes, que resolveria de forma diferente hoje:

- Sem autenticação — endpoints de escrita/exclusão são públicos
- Sem testes automatizados (validação feita manualmente via Postman)
- Recursos identificados por índice posicional, não por ID único
