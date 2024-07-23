<template>
    <nav class="navbar navbar-expand-md navbar-dark custom-bg-dark">
      <div class="container-fluid">
        <router-link class="navbar-brand" to="/">
          <img src="../assets/img/pokemonn.png" alt="Pikachu" height="40" class="d-inline-block align-text-center">
          PokeAPI
        </router-link>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item">
              <router-link class="nav-link" to="/">Home</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/about">About</router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </template>
  
  <style>
  .custom-bg-dark {
    background-color: #000000;
  }
  </style>
  
