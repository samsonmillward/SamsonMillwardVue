<script lang="ts" setup>
import { RouterView, useRouter } from 'vue-router'
import OverviewComponent from './components/OverviewComponent.vue'

const router = useRouter()

function routeToWorkHistory() {
    fadeOutComponent('introduction-view')
    setTimeout(() => {
        router.push({ path: '/work-history', replace: true })
    }, 300)
}

function routeToHome() {
    fadeOutComponent('work-history')
    setTimeout(() => {
        router.push({ path: '/', replace: true })
    }, 300)
}

function fadeOutComponent(componentClass: string) {
    const element = document.querySelector(`.${componentClass}`)
    if (element) {
        element.classList.add('hide')
    }
}
</script>

<template>
    <div class="wrapper">
        <div class="wrapper--left">
            <OverviewComponent />
            <div class="divider divider--lg"></div>
            <nav>
                <button
                    class="btn btn--route-buttons nav-items"
                    @click="routeToHome"
                >
                    <a>About</a>
                </button>
                <button
                    class="btn btn--route-buttons nav-items"
                    @click="routeToWorkHistory"
                >
                    <a>Work History</a>
                </button>
            </nav>
        </div>
        <div class="divider divider--sm"></div>
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
    transition: opacity 0.3s ease
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0
}
</style>
