# CodeGlance Vue Analysis Prompt

You are a senior Vue.js developer analyzing a Vue application to create comprehensive documentation that makes the component architecture, Composition API usage, state management, and Vue patterns immediately understandable.

## Input Repository
Analyze the Vue application at: [REPOSITORY_PATH]

## Your Mission
Create Vue-specific documentation that explains the component structure, reactivity system, routing, state management, and Vue 3 patterns in a way that developers can quickly understand and contribute.

## Output Structure

Generate the following files in `guide/vue/` directory:

### 1. guide/vue/overview.md
```markdown
# 🟢 Vue Application Guide

## 🎯 Quick Facts
- **Vue Version**: [2.x/3.x]
- **API Style**: [Options API/Composition API/Both]
- **Build Tool**: [Vite/Vue CLI/Webpack]
- **State Management**: [Vuex/Pinia/Custom]
- **Router**: [Vue Router version]
- **UI Framework**: [Vuetify/Element Plus/Quasar/PrimeVue/etc]
- **Testing**: [Vitest/Jest/Cypress]
- **TypeScript**: [Yes/No]

## 🏗️ Application Architecture
[High-level component architecture diagram]

## 📦 Key Dependencies
- [dependency]: [purpose]
- [dependency]: [purpose]
```

### 2. guide/vue/component-tree.md
```markdown
# 🌳 Component Hierarchy

## Visual Component Tree
```
App.vue
├── 📐 Layout/AppLayout.vue
│   ├── 🔝 components/AppHeader.vue
│   │   ├── NavMenu.vue
│   │   └── UserDropdown.vue
│   ├── 📊 views/Dashboard.vue      [Route: /dashboard]
│   │   ├── StatCard.vue
│   │   ├── ChartWidget.vue
│   │   └── DataTable.vue
│   ├── 👤 views/Profile.vue        [Route: /profile]
│   │   ├── ProfileForm.vue
│   │   └── AvatarUpload.vue
│   └── ⚙️ views/Settings.vue       [Route: /settings]
│       ├── SettingsTabs.vue
│       └── PreferenceForm.vue
└── 🔐 Auth/AuthLayout.vue
    ├── views/Login.vue              [Route: /login]
    └── views/Register.vue           [Route: /register]
```

## Component Categories

### 📄 Page Components (Views)
Located in `src/views/`:
- `Home.vue` - Landing page
- `Dashboard.vue` - Main application view
- `Profile.vue` - User profile page

### 🧩 Base Components
Located in `src/components/base/`:
- `BaseButton.vue` - Reusable button
- `BaseInput.vue` - Form input wrapper
- `BaseModal.vue` - Modal dialog

### 📦 Feature Components
Located in `src/components/[feature]/`:
- `UserList.vue` - User management
- `PostEditor.vue` - Content creation
- `CommentThread.vue` - Discussion threads

### 🎨 Layout Components
Located in `src/layouts/`:
- `DefaultLayout.vue` - Standard layout
- `AuthLayout.vue` - Authentication pages
- `AdminLayout.vue` - Admin panel
```

### 3. guide/vue/composition-api.md (for Vue 3)
```markdown
# 🪝 Composition API Patterns

## Composables Directory
```
src/composables/
├── useAuth.js         [Authentication logic]
├── useApi.js          [API calls]
├── useForm.js         [Form handling]
├── usePagination.js   [Pagination logic]
└── useDebounce.js     [Debounce utility]
```

## Key Composables

### `useAuth()`
```javascript
// composables/useAuth.js
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'

export function useAuth() {
  const user = ref(null)
  const isAuthenticated = computed(() => !!user.value)
  
  const login = async (credentials) => {
    const response = await api.login(credentials)
    user.value = response.user
    router.push('/dashboard')
  }
  
  const logout = () => {
    user.value = null
    router.push('/login')
  }
  
  return {
    user: readonly(user),
    isAuthenticated,
    login,
    logout
  }
}
```

### `useApi(url, options)`
```javascript
// composables/useApi.js
export function useApi(url, options = {}) {
  const data = ref(null)
  const error = ref(null)
  const loading = ref(false)
  
  const fetch = async () => {
    loading.value = true
    try {
      const response = await axios.get(url, options)
      data.value = response.data
    } catch (err) {
      error.value = err
    } finally {
      loading.value = false
    }
  }
  
  onMounted(() => {
    if (options.immediate !== false) {
      fetch()
    }
  })
  
  return { data, error, loading, refetch: fetch }
}
```

## Component Patterns

### Script Setup Syntax
```vue
<script setup>
import { ref, computed, watch } from 'vue'
import { useAuth } from '@/composables/useAuth'

// Props
const props = defineProps({
  title: String,
  count: { type: Number, default: 0 }
})

// Emits
const emit = defineEmits(['update', 'delete'])

// Composables
const { user, isAuthenticated } = useAuth()

// Reactive state
const localCount = ref(props.count)
const doubled = computed(() => localCount.value * 2)

// Watchers
watch(() => props.count, (newVal) => {
  localCount.value = newVal
})

// Methods
const handleClick = () => {
  emit('update', localCount.value + 1)
}
</script>
```
```

### 4. guide/vue/state-management.md
```markdown
# 🔄 State Management

## Pinia Store Structure (Vue 3)
```javascript
// stores/user.js
import { defineStore } from 'pinia'

export const useUserStore = defineStore('user', {
  state: () => ({
    currentUser: null,
    users: [],
    loading: false
  }),
  
  getters: {
    isAuthenticated: (state) => !!state.currentUser,
    userCount: (state) => state.users.length
  },
  
  actions: {
    async fetchUsers() {
      this.loading = true
      try {
        const response = await api.getUsers()
        this.users = response.data
      } finally {
        this.loading = false
      }
    }
  }
})
```

## Vuex Store Structure (Vue 2/3)
```javascript
// store/modules/user.js
export default {
  namespaced: true,
  
  state: {
    currentUser: null,
    users: []
  },
  
  mutations: {
    SET_USER(state, user) {
      state.currentUser = user
    },
    SET_USERS(state, users) {
      state.users = users
    }
  },
  
  actions: {
    async login({ commit }, credentials) {
      const user = await api.login(credentials)
      commit('SET_USER', user)
      return user
    }
  },
  
  getters: {
    isAuthenticated: state => !!state.currentUser
  }
}
```

## Store Usage in Components
```vue
<script setup>
// Pinia
import { useUserStore } from '@/stores/user'
const userStore = useUserStore()
const { currentUser, isAuthenticated } = storeToRefs(userStore)

// Vuex (Composition API)
import { useStore } from 'vuex'
const store = useStore()
const user = computed(() => store.state.user.currentUser)
</script>
```
```

### 5. guide/vue/routing.md
```markdown
# 🛣️ Vue Router Configuration

## Route Structure
```javascript
// router/index.js
const routes = [
  {
    path: '/',
    component: () => import('@/layouts/DefaultLayout.vue'),
    children: [
      {
        path: '',
        name: 'Home',
        component: () => import('@/views/Home.vue')
      },
      {
        path: 'dashboard',
        name: 'Dashboard',
        component: () => import('@/views/Dashboard.vue'),
        meta: { requiresAuth: true }
      }
    ]
  },
  {
    path: '/auth',
    component: () => import('@/layouts/AuthLayout.vue'),
    children: [
      {
        path: 'login',
        name: 'Login',
        component: () => import('@/views/Login.vue')
      }
    ]
  },
  {
    path: '/admin',
    component: () => import('@/layouts/AdminLayout.vue'),
    meta: { requiresAuth: true, role: 'admin' },
    children: [...]
  }
]
```

## Navigation Guards
```javascript
// Route protection
router.beforeEach((to, from, next) => {
  const { isAuthenticated } = useAuth()
  
  if (to.meta.requiresAuth && !isAuthenticated.value) {
    next('/login')
  } else if (to.meta.role && !hasRole(to.meta.role)) {
    next('/unauthorized')
  } else {
    next()
  }
})
```

## Programmatic Navigation
```javascript
// In components
const router = useRouter()
const route = useRoute()

// Navigate
router.push('/dashboard')
router.push({ name: 'Profile', params: { id: 123 } })

// Replace
router.replace('/login')

// Go back
router.back()
```
```

### 6. guide/vue/reactivity.md
```markdown
# ⚡ Reactivity System

## Reactive References
```javascript
import { ref, reactive, computed, watch } from 'vue'

// Ref for primitives
const count = ref(0)
const message = ref('Hello')

// Reactive for objects
const state = reactive({
  user: null,
  settings: {}
})

// Computed properties
const doubled = computed(() => count.value * 2)
const fullName = computed(() => 
  `${state.user?.firstName} ${state.user?.lastName}`
)

// Watchers
watch(count, (newVal, oldVal) => {
  console.log(`Count changed from ${oldVal} to ${newVal}`)
})

// Watch effect
watchEffect(() => {
  console.log(`Count is now: ${count.value}`)
})
```

## Reactivity Patterns

### toRefs for Destructuring
```javascript
const state = reactive({
  foo: 1,
  bar: 2
})

// ❌ This loses reactivity
const { foo, bar } = state

// ✅ This maintains reactivity
const { foo, bar } = toRefs(state)
```

### Shallow vs Deep Reactivity
```javascript
// Deep reactive (default)
const state = reactive({
  nested: { deep: { value: 1 } }
})

// Shallow reactive
const shallow = shallowReactive({
  nested: { deep: { value: 1 } }
})

// Shallow ref
const shallowArray = shallowRef([])
```
```

### 7. guide/vue/testing.md
```markdown
# 🧪 Testing Vue Components

## Component Testing
```javascript
// tests/components/UserCard.spec.js
import { mount } from '@vue/test-utils'
import { createPinia } from 'pinia'
import UserCard from '@/components/UserCard.vue'

describe('UserCard', () => {
  it('renders user name', () => {
    const wrapper = mount(UserCard, {
      props: {
        user: { name: 'John Doe', email: 'john@example.com' }
      }
    })
    
    expect(wrapper.text()).toContain('John Doe')
  })
  
  it('emits delete event', async () => {
    const wrapper = mount(UserCard, {
      props: { user: { id: 1 } }
    })
    
    await wrapper.find('.delete-btn').trigger('click')
    
    expect(wrapper.emitted()).toHaveProperty('delete')
    expect(wrapper.emitted().delete[0]).toEqual([1])
  })
})
```

## Composable Testing
```javascript
// tests/composables/useCounter.spec.js
import { useCounter } from '@/composables/useCounter'

describe('useCounter', () => {
  it('increments count', () => {
    const { count, increment } = useCounter()
    
    expect(count.value).toBe(0)
    increment()
    expect(count.value).toBe(1)
  })
})
```

## E2E Testing with Cypress
```javascript
// cypress/e2e/login.cy.js
describe('Login Flow', () => {
  it('logs in successfully', () => {
    cy.visit('/login')
    cy.get('[data-cy=email]').type('user@example.com')
    cy.get('[data-cy=password]').type('password')
    cy.get('[data-cy=submit]').click()
    
    cy.url().should('include', '/dashboard')
    cy.contains('Welcome back')
  })
})
```
```

### 8. guide/vue/performance.md
```markdown
# ⚡ Performance Optimization

## Component Optimization

### Lazy Loading
```javascript
// Route-level lazy loading
const Dashboard = () => import('@/views/Dashboard.vue')

// Component-level lazy loading
import { defineAsyncComponent } from 'vue'

const AsyncModal = defineAsyncComponent(() =>
  import('@/components/Modal.vue')
)
```

### List Rendering Optimization
```vue
<template>
  <!-- Use unique keys -->
  <div v-for="item in items" :key="item.id">
    {{ item.name }}
  </div>
  
  <!-- Virtual scrolling for large lists -->
  <virtual-list :items="largeList" :item-height="50">
    <template #default="{ item }">
      <ItemComponent :item="item" />
    </template>
  </virtual-list>
</template>
```

### Computed vs Methods
```javascript
// ✅ Use computed for derived state (cached)
const filtered = computed(() => 
  items.value.filter(item => item.active)
)

// ❌ Avoid methods for derived state (recalculated every render)
const filtered = () => 
  items.value.filter(item => item.active)
```

## Bundle Optimization
```javascript
// vite.config.js
export default {
  build: {
    rollupOptions: {
      output: {
        manualChunks: {
          vendor: ['vue', 'vue-router', 'pinia'],
          ui: ['element-plus']
        }
      }
    }
  }
}
```
```

### 9. guide/vue/directives-plugins.md
```markdown
# 🔧 Custom Directives & Plugins

## Custom Directives
```javascript
// directives/focus.js
export const vFocus = {
  mounted(el) {
    el.focus()
  }
}

// directives/click-outside.js
export const vClickOutside = {
  mounted(el, binding) {
    el.clickOutsideEvent = (event) => {
      if (!(el === event.target || el.contains(event.target))) {
        binding.value(event)
      }
    }
    document.addEventListener('click', el.clickOutsideEvent)
  },
  unmounted(el) {
    document.removeEventListener('click', el.clickOutsideEvent)
  }
}

// Usage in components
<input v-focus />
<div v-click-outside="handleClickOutside">...</div>
```

## Global Plugins
```javascript
// plugins/i18n.js
export default {
  install(app, options) {
    app.config.globalProperties.$t = (key) => {
      return translations[options.locale][key] || key
    }
  }
}

// main.js
import i18nPlugin from './plugins/i18n'

app.use(i18nPlugin, { locale: 'en' })
```

## Provide/Inject Pattern
```javascript
// Parent component
provide('theme', ref('dark'))

// Child component (any level deep)
const theme = inject('theme', ref('light')) // with default
```
```

## Analysis Focus Areas

### 1. Component Architecture
- Component hierarchy mapping
- Props/events communication
- Slot usage patterns
- Component reusability

### 2. Reactivity Analysis
- Reactive data patterns
- Computed properties usage
- Watcher implementation
- Performance implications

### 3. State Management
- Store organization
- Action/mutation patterns
- Module structure
- State shape optimization

### 4. Performance Review
- Bundle size analysis
- Lazy loading implementation
- Re-render optimization
- Memory leak detection

## Success Metrics

After reading the Vue documentation, a developer should:
- ✅ Understand component architecture
- ✅ Know state management approach
- ✅ Understand routing structure
- ✅ Be able to create new components
- ✅ Know Vue 3 Composition API patterns
- ✅ Understand testing strategies

Generate the Vue-specific documentation for [REPOSITORY_PATH] now.