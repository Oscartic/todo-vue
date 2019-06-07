<template>
  <div id="app">
    <b-container>
      <b-row>
        <b-nav tabs>
          <b-nav-item exact to="/todos">Listado de todos</b-nav-item>
          <b-nav-item exact to="/todos/create">Formulario de todos</b-nav-item>
        </b-nav>
      
      
      </b-row>
      <router-view/>
    </b-container>
  </div>
</template>
