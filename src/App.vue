<template>
  <div id="app">
    <b-container>
      <b-navbar toggleable="md" type="dark" variant="info">
        <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
        <b-navbar-brand href="/">Make it Fast!</b-navbar-brand>
        <b-collapse is-nav id="nav_collapse">
          <b-navbar-nav>
            <b-nav-item>
              <router-link class="nav-link" to="/">Lista</router-link>
            </b-nav-item>
          </b-navbar-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-form>
            </b-nav-form>
            <b-nav-item-dropdown text="Lang" right>
              <b-dropdown-item href="#">EN</b-dropdown-item>
              <b-dropdown-item href="#">ES</b-dropdown-item>
              <b-dropdown-item href="#">RU</b-dropdown-item>
              <b-dropdown-item href="#">FA</b-dropdown-item>
            </b-nav-item-dropdown>
            <!-- <b-nav-item-dropdown right> -->
              <!-- Using button-content slot -->
              <!-- <b-dropdown-item href="#">Profile</b-dropdown-item> -->
              <!-- <b-dropdown-item href="#">Signout</b-dropdown-item> -->
            <!-- </b-nav-item-dropdown> -->
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
      <router-view/>
    </b-container>
  </div>
</template>