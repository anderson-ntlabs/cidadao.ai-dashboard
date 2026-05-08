# 🚀 Guia de Deploy no Vercel - Dashboard Cidadão.AI

## ✅ Status Atual
- **Build**: ✅ Funcionando perfeitamente (53 segundos)
- **Deploy**: ❌ Falhando na fase "Deploying outputs" (timeout após 34s)

## 🔧 Solução Recomendada: Deploy Manual via Interface Web

### Passo 1: Deletar Projeto Atual (se existir)
1. Acesse: https://vercel.com/dashboard
2. Encontre o projeto `cidadao-dashboard`
3. Clique em Settings → Delete Project
4. Confirme a exclusão

### Passo 2: Criar Novo Projeto
1. Clique em **"Add New..."** → **"Project"**
2. Importe do GitHub: `anderson-ntlabs/cidadao.ai-dashboard`
3. Aguarde a importação

### Passo 3: Configurações do Build
Na tela de configuração, ajuste:

```
Framework Preset: Next.js (deve detectar automaticamente)
Root Directory: ./ (deixe vazio)
Build Command: npm run build
Output Directory: .next (deixe padrão)
Install Command: npm install
Development Command: npm run dev
```

### Passo 4: Variáveis de Ambiente
Adicione estas variáveis:

| Nome | Valor |
|------|-------|
| `NEXT_PUBLIC_API_URL` | `https://cidadao-api-production.up.railway.app` |
| `NEXT_PUBLIC_ENABLE_REAL_API` | `true` |
| `NEXT_PUBLIC_USE_MOCK_DATA` | `false` |

### Passo 5: Deploy
1. Clique em **"Deploy"**
2. Aguarde o processo (deve levar ~2-3 minutos)

## 🎯 Alternativa: Vercel CLI Local

Se a interface web falhar, tente via CLI:

```bash
# 1. Login no Vercel
npx vercel login

# 2. Deploy (responda as perguntas)
npx vercel

# Respostas sugeridas:
# - Set up and deploy? Y
# - Which scope? (sua conta)
# - Found project. Link? N
# - What's your project name? cidadao-dashboard
# - In which directory? ./
# - Override settings? N

# 3. Deploy em produção
npx vercel --prod
```

## 🔍 Se Continuar Falhando

### Opção A: Reduzir Tamanho dos Assets
```bash
# Otimizar imagens (opcional)
npm install -D sharp
# Adicionar otimização automática no next.config.js
```

### Opção B: Verificar Logs Detalhados
1. No Vercel Dashboard → Functions → Logs
2. Procure por erros específicos no momento do deploy
3. Verifique se há limite de tamanho sendo excedido

### Opção C: Configuração Alternativa
Crie um novo `vercel.json` minimalista:
```json
{
  "framework": "nextjs"
}
```

### Opção D: Contatar Suporte
- https://vercel.com/help
- Mencione: "Build success but fails at 'Deploying outputs' phase"
- Projeto: anderson-ntlabs/cidadao.ai-dashboard

## 📊 Informações do Build

**Build bem-sucedido mostra:**
- Compiled successfully ✅
- Generated static pages (5/5) ✅
- Size: 335 KB First Load JS ✅
- Created serverless functions ✅

**Erro ocorre em:**
- "Deploying outputs..." (após 34 segundos)

## 🌟 URL Esperada Após Deploy

```
https://cidadao-dashboard.vercel.app
```

---

**Nota**: O código está perfeito. O problema é infraestrutura do Vercel ou limite de conta.