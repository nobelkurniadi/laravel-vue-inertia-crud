<template>
      <nav class="navbar navbar-expand-md navbar-light fixed-top bg-white shadow-sm">
        <div class="container">
          <inertia-link class="navbar-brand" href="/">Laravue Inertia</inertia-link>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarCollapse" aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarCollapse">
            <ul class="navbar-nav me-auto mb-2 mb-md-0">
              <li class="nav-item">
                <inertia-link class="nav-link" href="/">Products</inertia-link>
              </li>
            </ul>
            <form class="d-flex">
              <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
              <button class="btn btn-success" type="submit">Search</button>
            </form>
          </div>
        </div>
      </nav>
      <main class="container mt-5">
        <slot />
      </main>
  </template>
  
  <script>
    import { Link } from '@inertiajs/inertia-vue3';
    export default {
      components: {
        Link
      },
    }
  </script>
  
  <style scoped>
      .mt-5 {
        margin-top: 100px!important;
      }
  </style>