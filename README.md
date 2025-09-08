# Git Workflow - SAFeR

Guia completo de fluxo de branches e comandos Git para o projeto **SAFeR**, seguindo boas práticas de desenvolvimento.

---

## Estrutura de Branches

| Branch | Descrição |
|--------|-----------|
| `main` | Código estável, pronto para produção. |
| `develop` | Branch principal de desenvolvimento contínuo. |
| `release/x.x` | Preparação de uma versão específica. |
| `feature/nome-da-feature` | Nova funcionalidade ou melhoria. |
| `bugfix/nome-do-bug` | Correção rápida de bug. |

---

## 📊 Diagrama do Fluxo de Branches (Visual)

         🌟 main
           ▲
           │
        🔀 Merge Release
           │
       🏷 release/1.0
           ▲
           │
        🔧 develop
       ┌───────────────────────┐
       │                       │
       ✨feature/login        ✨feature/pagamento
       │                       │
       └───────▲───────────────┘
               │
          🔀 Merge Feature
          
main: branch estável, pronta para produção.

release/x.x: prepara a versão final antes de enviar para main.

develop: branch de desenvolvimento contínuo, integra features antes do release.

feature/nome: novas funcionalidades que são desenvolvidas isoladamente e depois integradas (merge) em develop.

Os ícones ajudam a identificar o propósito de cada branch.
          
**Legenda:**
- 🔀 = merge  
- 🆕 = novas funcionalidades  
- 🐞 = correção de bugs  
- 🌟 = branch principal / produção  
- 🔧 = branch de desenvolvimento  

---

# Comandos Git

# Puxa as alterações da branch atual do repositório remoto
git pull origin nome-da-branch

## 1. Iniciar repositório ##
git init
git add .
git commit -m "Commit inicial"

## 2. Criar branch de desenvolvimento ##
git checkout -b develop

## 3. Criar branch de release ## 
git checkout -b release/1.0 develop

## 4. Criar branches de feature ##
git checkout develop
git checkout -b feature/readme-inicial
git checkout -b feature/transacao
git checkout -b feature/alerta-fraude

## 5. Criar branch de bugfix ##
git checkout develop
git checkout -b bugfix/correcao-alerta

## 6. Entrar em uma branch existente ##
git checkout nome-da-branch
# exemplo: git checkout feature/readme-inicial

## 7. Voltar para main ou develop ##
git checkout main
git checkout develop

## 8. Merge de feature ou release ##
### Merge feature para develop
git checkout develop
git merge feature/readme-inicial
### Merge release para main
git checkout main
git merge release/1.0

## 9. Deletar branch local
git branch -d feature/readme-inicial
git branch -d release/1.0

## 10. Push para GitHub
git push -u origin main
git push -u origin develop
git push -u origin feature/readme-inicial
git push -u origin release/1.0
## Para branches futuras
git push -u origin nome-da-branch

## Dicas rápidas
### - Trabalhe em branches de feature e só faça merge quando testado.
### - Teste a release antes de mesclar na main.
### - Use nomes claros e delete branches antigas para manter o repositório limpo.
