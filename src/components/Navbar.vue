<template>
  <div>
    <div>
      <b-navbar toggleable="lg" type="dark" variant="dark">
        <b-navbar-brand href="#">CG</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item :to="{name: 'home'}">Home</b-nav-item> 
            <b-nav-item :to="{name: 'contact'}">Contacts</b-nav-item> 
            <b-nav-item :to="{name: 'projects'}">Projects</b-nav-item> 
          </b-navbar-nav>

        </b-collapse>
      </b-navbar>
    </div>


  </div>
</template>

<script>


export default {
  name: 'Navbar'
}
</script>

<style>

</style>

