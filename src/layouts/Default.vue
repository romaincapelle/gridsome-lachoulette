<template>
  <div class="layout">
    <header class="header">
      <g-image alt="Logo Choulette" src="~/favicon.png" width="35" />

      <strong>
        <h1>Bienvenue sur le drive de La Choulette</h1>
        <p>
          Du lundi au vendredi de 8h à 12h et de 14h à 18h + le samedi matin de
          9h à 12h
        </p>
      </strong>
    </header>
    <hr />
    <br />
    <slot />
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style>
body {
  font-family: -apple-system, system-ui, BlinkMacSystemFont, 'Segoe UI', Roboto,
    'Helvetica Neue', Arial, sans-serif;
  margin: 0;
  padding: 0;
  line-height: 1.5;
}

.layout {
  max-width: 760px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;
}

.nav__link {
  margin-left: 20px;
}

.center {
  text-align: center;
}
.legal {
  margin: 40px auto;
  padding: 15px;
  font-size: 8px;
  border: solid 1px black;
  line-height: 15px;
}

input {
  width: 100%;
  padding: 7px 18px;
  font-size: 15px;
  margin-top: 5px;
  margin-bottom: 28px;
}

button {
  width: 100%;
  padding: 20px;
  background-color: #ebb716;
  font-size: 17px;
  color: #242424;
  border-radius: 7 px;
}

button:hover {
  width: 100%;
  padding: 20px;
  background-color: white;
  font-size: 17px;
  color: #ebb716;
  border: 1px solid #242424;
  cursor: pointer;
}

textarea {
  width: 100%;
  padding: 20px 18px;
  font-size: 15px;
  margin-top: 5px;
  margin-bottom: 28px;
}
</style>
