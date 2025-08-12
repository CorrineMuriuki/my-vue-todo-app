# Moringa School AI Capstone Project -Vue.js Beginner's ToolKit and Simple App
# Getting Started with Vue.js – A Beginner's Interactive Todo App Guide

## 1. Title & Objective

**Technology Chosen:** Vue.js 3 (Progressive JavaScript Framework)

**Why Vue.js?**
- Gentle learning curve compared to React or Angular
- Excellent documentation and community support
- Perfect balance between simplicity and power
- Great for building interactive web applications

**End Goal:** Create an interactive Todo List application that demonstrates Vue.js core concepts including components, reactivity, event handling, and conditional rendering.

## 2. Quick Summary of the Technology

**What is Vue.js?**
Vue.js is a progressive JavaScript framework for building user interfaces. Unlike other monolithic frameworks, Vue is designed from the ground up to be incrementally adoptable.

**Where is it used?**
- Single Page Applications (SPAs)
- Progressive Web Apps (PWAs)
- Component libraries
- Interactive website features

**Real-world example:** GitLab uses Vue.js for their frontend, and companies like Adobe, Nintendo, and BMW have adopted Vue.js for various projects.

## 3. System Requirements

**Operating System:** Windows, macOS, or Linux

**Required Tools:**
- **Node.js** (version 16.0 or higher)
- **npm** (comes with Node.js) or **yarn**
- **Code Editor:** VS Code (recommended)
- **Web Browser:** Chrome, Firefox, Safari, or Edge

**Recommended VS Code Extensions:**
- Vetur or Volar (Vue Language Support)
- Auto Rename Tag
- Bracket Pair Colorizer

## 4. Installation & Setup Instructions

### Step 1: Verify Node.js Installation
```bash
node --version
npm --version
```

### Step 2: Create a New Vue.js Project
```bash
# Using Vue CLI (recommended for beginners)
npm install -g @vue/cli
vue create my-vue-todo-app

# Or using Vite (faster alternative)
npm create vue@latest my-vue-todo-app
```

### Step 3: Navigate and Start Development Server
```bash
cd my-vue-todo-app
npm run dev
```

### Step 4: Project Structure Overview
```
my-vue-todo-app/
├── public/
├── src/
│   ├── components/
│   ├── App.vue
│   └── main.js
├── package.json
└── README.md
```

## 5. Minimal Working Example - Interactive Todo App

### Description
Our example creates a simple but functional todo list application that demonstrates:
- Data binding
- Event handling
- Conditional rendering
- List rendering
- Component composition

### Main App Component (src/App.vue)
```vue
<template>
  <div id="app">
    <h1>Vue.js Todo App</h1>
    
    <!-- Add Todo Form -->
    <div class="add-todo">
      <input
        v-model="newTodo"
        @keyup.enter="addTodo"
        placeholder="Add a new todo..."
        class="todo-input"
      >
      <button @click="addTodo" class="add-btn">Add</button>
    </div>

    <!-- Todo List -->
    <ul class="todo-list" v-if="todos.length > 0">
      <li
        v-for="todo in todos"
        :key="todo.id"
        :class="{ completed: todo.completed }"
        class="todo-item"
      >
        <input
          type="checkbox"
          v-model="todo.completed"
          class="todo-checkbox"
        >
        <span class="todo-text">{{ todo.text }}</span>
        <button @click="removeTodo(todo.id)" class="delete-btn">×</button>
      </li>
    </ul>

    <!-- Empty State -->
    <p v-else class="empty-state">No todos yet. Add one above!</p>

    <!-- Stats -->
    <div class="stats" v-if="todos.length > 0">
      <p>Total: {{ todos.length }} | Completed: {{ completedCount }} | Remaining: {{ remainingCount }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      newTodo: '',
      todos: []
    }
  },
  computed: {
    completedCount() {
      return this.todos.filter(todo => todo.completed).length
    },
    remainingCount() {
      return this.todos.filter(todo => !todo.completed).length
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({
          id: Date.now(),
          text: this.newTodo.trim(),
          completed: false
        })
        this.newTodo = ''
      }
    },
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  }
}
</script>

<style>
#app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

.add-todo {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.todo-input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 16px;
}

.add-btn {
  padding: 10px 20px;
  background: #42b883;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.add-btn:hover {
  background: #369870;
}

.todo-list {
  list-style: none;
  padding: 0;
}

.todo-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px;
  border: 1px solid #eee;
  border-radius: 4px;
  margin-bottom: 5px;
}

.todo-item.completed {
  opacity: 0.6;
}

.todo-item.completed .todo-text {
  text-decoration: line-through;
}

.todo-checkbox {
  width: 18px;
  height: 18px;
}

.todo-text {
  flex: 1;
}

.delete-btn {
  background: #ff6b6b;
  color: white;
  border: none;
  border-radius: 50%;
  width: 25px;
  height: 25px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.delete-btn:hover {
  background: #ff5252;
}

.empty-state {
  text-align: center;
  color: #666;
  font-style: italic;
  margin: 40px 0;
}

.stats {
  text-align: center;
  margin-top: 20px;
  color: #666;
  font-size: 14px;
}
</style>
```

### Expected Output
When you run the application, you should see:
1. A clean interface with "Vue.js Todo App" title
2. An input field and "Add" button
3. The ability to add todos by typing and pressing Enter or clicking Add
4. Checkboxes to mark todos as complete
5. Delete buttons (×) to remove todos
6. Statistics showing total, completed, and remaining todos

## 6. AI Prompt Journal

### Prompt 1: Project Setup
**Prompt used:** "Guide me through setting up a new Vue.js 3 project from scratch, including the recommended tools and project structure"

**AI's response summary:** The AI provided comprehensive setup instructions using Vue CLI, explained the project structure, and recommended essential VS Code extensions for Vue development.

**Evaluation:** Very helpful - provided both CLI and Vite options, explained the reasoning behind recommendations.

### Prompt 2: Core Concepts
**Prompt used:** "Explain Vue.js core concepts like data binding, computed properties, and methods with simple examples"

**AI's response summary:** The AI explained reactive data, v-model for two-way binding, computed properties for derived state, and methods for event handling with clear code examples.

**Evaluation:** Excellent - clear explanations with practical examples that directly applied to the todo app.

### Prompt 3: Component Architecture
**Prompt used:** "How do I create a single-file Vue component with template, script, and style sections for a todo list application?"

**AI's response summary:** The AI demonstrated the .vue file structure, explained the separation of concerns, and showed how to implement reactive data and event handling in a todo context.

**Evaluation:** Perfect for the project - provided the exact structure needed for the capstone deliverable.

### Prompt 4: Debugging Help
**Prompt used:** "My Vue.js todo app isn't updating when I add new items. What are common reactivity issues and how do I fix them?"

**AI's response summary:** The AI explained Vue's reactivity system, common pitfalls like direct array index assignment, and provided solutions using proper Vue methods.

**Evaluation:** Critical for troubleshooting - saved significant debugging time and taught important Vue concepts.

## 7. Common Issues & Fixes

### Issue 1: "Vue is not defined" Error
**Problem:** Import error when trying to use Vue in components
**Solution:** Ensure proper import statement:
```javascript
import { createApp } from 'vue'
```

### Issue 2: Data Not Updating in Template
**Problem:** Changes to data properties not reflecting in the UI
**Solution:** Ensure data is returned as a function:
```javascript
data() {
  return {
    // your data here
  }
}
```

### Issue 3: Event Handlers Not Working
**Problem:** Click events or form submissions not triggering methods
**Solution:** Check method binding syntax:
```vue
<button @click="methodName">Click me</button>
<!-- NOT onclick="methodName" -->
```

### Issue 4: CSS Not Applied to Components
**Problem:** Styles not showing up in single-file components
**Solution:** Ensure `<style>` tag is properly placed and consider using `scoped` attribute:
```vue
<style scoped>
/* Component-specific styles */
</style>
```

### Issue 5: Dev Server Not Starting
**Problem:** `npm run dev` fails or shows errors
**Solution:** 
1. Clear node_modules: `rm -rf node_modules package-lock.json`
2. Reinstall: `npm install`
3. Check Node.js version compatibility

## 8. References

**Official Documentation:**
- [Vue.js Official Guide](https://vuejs.org/guide/)
- [Vue.js API Reference](https://vuejs.org/api/)

**Video Tutorials:**
- [Vue.js Crash Course by Traversy Media](https://www.youtube.com/watch?v=qZXt1Aom3Cs)
- [Vue.js Tutorial for Beginners](https://www.youtube.com/watch?v=FXpIoQ_rT_c)

**Helpful Resources:**
- [Vue.js Examples & Demos](https://vuejs.org/examples/)
- [Vue.js Style Guide](https://vuejs.org/style-guide/)
- [Awesome Vue.js](https://github.com/vuejs/awesome-vue)
- [Vue.js DevTools Browser Extension](https://devtools.vuejs.org/)

**Community & Support:**
- [Vue.js Discord Community](https://discord.com/invite/HBherRA)
- [Vue.js Forum](https://forum.vuejs.org/)
- [Stack Overflow - Vue.js Tag](https://stackoverflow.com/questions/tagged/vue.js)

---

*This toolkit was created using AI-assisted learning prompts and hands-on experimentation. The goal is to provide a clear, replicable path for beginners to start their Vue.js journey.*
