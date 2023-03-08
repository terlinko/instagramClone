<template>
  <div>
    <NavBar />
    <MainComponent />
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import MainComponent from '@/components/MainComponent.vue'
export default {
    name: 'MainView',
    components: {
        NavBar,MainComponent
    },
    data(){
        return{

        }
    },
    methods:{

    }

}
</script>

<style>

</style>