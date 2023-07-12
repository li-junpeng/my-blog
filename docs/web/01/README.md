## vue3 + vite4 动态加载组件

更新时间: {docsify-updated}

versions:
- vue: 3.3.4
- vite: 4.3.9

```javascript
<script setup lang="ts">
    import { shallowRef, defineAsyncComponent } from 'vue'

    const coms = {
        com1: () => import('@/components/1.vue'),
        com2: () => import('@/components/2.vue'),
        com3: () => import('@/components/3.vue')
    }
    
    const formComponent = shallowRef(null)

    const onClick = (comKey: number) => {
        const component = coms[`com${comKey}`]
        if (component) {
            component().then(() => {
                formComponent.value = defineAsyncComponent(component)
            }).catch(() => {
                alert('组件加载失败')
            })    
        }
    }
</script>

<template>
    <button @click="onClick(1)">组件1</button>
    <button @click="onClick(2)">组件2</button>
    <button @click="onClick(3)">组件3</button>
    <component :is="formComponent"/>
</template>
```
