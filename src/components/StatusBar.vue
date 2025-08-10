<template>
    <div class="status-bar" :class="{ 'dark-theme': isDarkTheme }">
        <span>{{ statusText }}</span>
    </div>
</template>

<script setup lang="ts">
import { computed, ref, inject, type Ref } from "vue";

// 注入主题状态
const isDarkTheme = inject("isDarkTheme", ref(false)) as Ref<boolean>;

const props = defineProps<{
    content: string;
}>();

const statusText = computed(() => {
    const content = props.content;
    const words = content.trim().split(/\s+/).length;
    const chars = content.length;
    return `${words}字，${chars}字符`;
});
</script>

<style scoped>
.status-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 8px 16px;
    background: #f8f8f8;
    border-top: 1px solid #e0e0e0;
    font-size: 12px;
    color: #666;
}

.status-bar.dark-theme {
    background: #252525;
    border-top-color: #444;
    color: #999;
}
</style>
