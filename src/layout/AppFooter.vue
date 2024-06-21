
<template>
    <div class="layout-footer">
        <p>&copy; 2024 BitsFlow Technologies Pvt Ltd. All rights reserved.</p>
    </div>
</template>
<style lang="scss" scoped>

.layout-footer {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    padding: 4px;
    z-index: 1000; 
}

.layout-footer {
    background: var(--surface-card);
    border: 1px solid var(--surface-border);
    box-shadow: var(--card-shadow);
    
    &.dark-theme {
        background: var(--dark-surface-card);
        border-color: var(--dark-surface-border);
        box-shadow: var(--dark-card-shadow);
    }
}


</style>
