<template>
  <div id="app">
    <navbar></navbar>
    <editor></editor>
    <footer-comp></footer-comp>

    <notifications />
  </div>
</template>

<script>
  import Navbar from './components/Navbar'
  import FooterComp from './components/Footer-comp'
  import Editor from './components/Editor'

  export default {
    name: 'app',
    components: {
      Navbar,
      FooterComp,
      Editor
    },
    mounted () {
      let mutationsToSubscribe = [
        'changeLanguage',
        'updateCode',
        'uploadCode',
        'resetCode',
        'changeTheme',
        'changeFont',
        'changeFontSize',
        'resetEditor',
        'satCode',
        'changeAutosave'
      ]

      this.$store.subscribe((mutation, state) => {
        if (mutationsToSubscribe.includes(mutation.type) && !state.isChanged) {
          this.$store.commit('setIsChanged', true)
        }
      })
    }
  }

</script>
<style src="bootstrap/dist/css/bootstrap.css"></style>
<style src="font-awesome/css/font-awesome.css"></style>
<style src="./assets/css/whole.css"></style>
