# Projeto: Almoxarifado Web App — Backend (Node + SQLite) + Frontend (React) + PWA
- Subir projeto local: `railway up` (deploy local rápido)


### 4) After deploy — como apontar o frontend (PWA) para o backend


- Pegue a URL pública do backend (ex: `https://almox-backend-production.up.railway.app`) e configure `REACT_APP_API_BASE` com essa URL no build do frontend antes de `npm run build`.
- Re-build do frontend e faça deploy.


---


## 2) APK (Capacitor) — arquivos e passo-a-passo


Vou te entregar a pasta `mobile/` pronta para compilar. O fluxo que preparei é com **Capacitor** (opção A que você escolheu).


### Estrutura `mobile/`


```
mobile/
├─ package.json
├─ capacitor.config.json
├─ www/ (aqui vai o build do frontend — arquivos estáticos)
└─ android/ (projeto Android gerado após `npx cap add android`)
```


### `mobile/package.json`


```json
{
"name": "almox-mobile",
"version": "1.0.0",
"scripts": {
"prepare:web": "npm --prefix ../frontend run build && rm -rf www && cp -r ../frontend/dist www",
"android": "npx cap add android || true && npx cap sync android && npx cap open android"
},
"dependencies": {
"@capacitor/core": "^5.0.0",
"@capacitor/cli": "^5.0.0"
}
}
```


> Ajuste o caminho `../frontend/dist` para `../frontend/build` se usar CRA.


### `capacitor.config.json`


```json
{
"appId": "br.almoxarifado.app",
"appName": "Almoxarifado",
"webDir": "www",
"bundledWebRuntime": false
}
```
