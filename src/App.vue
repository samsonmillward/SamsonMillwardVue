<script lang="ts" setup>
import { RouterLink, RouterView } from 'vue-router'
import OverviewComponent from './components/OverviewComponent.vue'
</script>

<template>
    <div class="wrapper">
        <div class="wrapper--left">

            <OverviewComponent />
            <div class="divider"></div>
            <nav>
                <RouterLink to="/">Home</RouterLink>
                <RouterLink to="/work-history">Work History</RouterLink>
            </nav>
        </div>
        <div class="wrapper--right">
            <transition name="fade">
                <RouterView />
            </transition>
        </div>
    </div>

</template>


<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: opacity 3s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>
