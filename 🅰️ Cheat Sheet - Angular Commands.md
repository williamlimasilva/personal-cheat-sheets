# 🅰️ Cheat Sheet - Angular Commands

> 📝 **Guia completo de comandos e conceitos fundamentais do Angular, framework de desenvolvimento web baseado em TypeScript.**

---

## 📑 Índice

1. [Conceitos Básicos](#conceitos-básicos)
2. [Instalação e Configuração](#instalação-e-configuração)
3. [Sintaxe Fundamental](#sintaxe-fundamental)
4. [Estruturas Principais](#estruturas-principais)
5. [Recursos Avançados](#recursos-avançados)
6. [Melhores Práticas](#melhores-práticas)
7. [Links Úteis](#links-úteis)

---

## 📘 Conceitos Básicos

### 🔑 Fundamentos do Angular

| Conceito     | Descrição           | Exemplo   | Observação     |
| ------------ | ------------------- | --------- | -------------- |
| `Componente` | Bloco de construção básico que controla uma parte da tela | `@Component()` | Encapsula template, lógica e estilo |
| `Diretiva`   | Estende o comportamento de elementos HTML | `*ngIf`, `*ngFor` | Manipula DOM dinamicamente |
| `Serviço`    | Classe para compartilhar dados e funcionalidades | `@Injectable()` | Promove reutilização e injeção de dependência |

---

## 🔧 Instalação e Configuração

### 💻 Requisitos do Sistema

| Requisito     | Versão Mínima | Versão Recomendada | Observação     |
| ------------- | ------------- | ------------------ | -------------- |
| `Node.js`     | 14.x          | 16.x ou superior   | Necessário para npm |
| `TypeScript`  | 4.4.x         | 4.6.x ou superior  | Linguagem base |
| `Angular CLI` | 13.x          | 14.x ou superior   | Ferramenta de desenvolvimento |

### 📥 Processo de Instalação

```bash
# Instalar Angular CLI globalmente
npm install -g @angular/cli

# Criar novo projeto Angular
ng new meu-projeto-angular

# Servir aplicação localmente
ng serve

# Gerar novo componente
ng generate component meu-componente
```

---

## 🚀 Sintaxe Fundamental

### 📝 Estruturas Básicas

| Estrutura     | Descrição           | Exemplo   | Resultado |
| ------------- | ------------------- | --------- | --------- |
| `Interpolação` | Exibe valor de variável no template | `{{ titulo }}` | Mostra valor da variável |
| `Property Binding` | Vincula propriedade de elemento a uma expressão | `[propriedade]="valor"` | Atualiza dinamicamente |

### 💡 Exemplos Práticos

```typescript
@Component({
  selector: 'app-exemplo',
  template: `
    <h1>{{ titulo }}</h1>
    <button [disabled]="isDisabled">Clique</button>
  `
})
export class ExemploComponent {
  titulo = 'Meu Primeiro Componente';
  isDisabled = false;
}
```

---

## 🔍 Estruturas Principais

### 📊 Componentes e Módulos

| Componente     | Descrição           | Uso         | Exemplo   |
| -------------- | ------------------- | ----------- | --------- |
| `@Component`   | Define um componente | Decorator   | `@Component({ selector: 'app-root' })` |
| `@NgModule`    | Agrupa componentes relacionados | Configuração | `@NgModule({ declarations: [...] })` |

---

## 🎯 Recursos Avançados

### ⚡ Funcionalidades Avançadas

| Recurso     | Descrição           | Exemplo   | Observação     |
| ----------- | ------------------- | --------- | -------------- |
| `Lazy Loading` | Carregamento sob demanda de módulos | `loadChildren` | Melhora performance |
| `Reactive Forms` | Formulários reativos com validação | `FormBuilder` | Controle avançado de formulários |

---

## 📚 Melhores Práticas

### ✅ Recomendações

| Prática     | Descrição           | Exemplo   | Benefício           |
| ----------- | ------------------- | --------- | ------------------- |
| `Serviços`  | Usar serviços para lógica de negócio | `@Injectable()` | Desacoplamento |
| `OnPush`    | Estratégia de detecção de mudanças | `ChangeDetectionStrategy.OnPush` | Otimização de performance |

---

## 📑 Dicas e Alertas

> [!NOTE]
> Sempre use tipagem forte com TypeScript.

> [!WARNING]
> Evite lógica complexa em templates.

> [!TIP]
> Utilize Angular CLI para tarefas repetitivas.

---

## 🔗 Links Úteis

- [📘 Documentação Oficial Angular](https://angular.io/docs)
- [📚 Angular CLI](https://cli.angular.io/)
- [💻 Repositório GitHub](https://github.com/angular/angular)
- [👥 Comunidade Angular](https://angular.io/community)

---

## 🎨 Markdown Avançado

### Tabelas Comparativas

| Recurso | Básico | Avançado | Descrição   |
| ------- | ------ | -------- | ----------- |
| Componentes | ✅ | ✅ | Estrutura básica |
| Serviços | ❌ | ✅ | Injeção de dependência |

### Lista de Tarefas

- [x] Aprender conceitos básicos
- [ ] Dominar Angular avançado
- [ ] Criar projeto complexo

---

## 📜 Regras Adicionais

### Para Desenvolvimento Angular

1. Use sempre TypeScript
2. Siga princípios de componentização
3. Mantenha componentes pequenos e focados
4. Utilize lazy loading para performance
5. Implemente tratamento de erros consistente

---

## 🎉 Considerações Finais

### Diretrizes de Qualidade

- Manter código limpo e organizado
- Seguir padrões de arquitetura Angular
- Documentar componentes e serviços
- Realizar testes unitários e de integração
- Manter-se atualizado com novas versões

### Resultado Esperado

- Aplicações escaláveis
- Código manutenível
- Performance otimizada
- Experiência de desenvolvimento produtiva
