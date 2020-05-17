<template>
  <Layout>
    <h5>
      Nous avons recu votre commande et nous vous attendons a la brasserie.
    </h5>
    <h4>16 Rue des Écoles 59111 Hordain</h4>
    <p>Pour toute questions, veuillez nous contacter au +33 3 27 35 72 44</p>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: 'About us',
  },
};
</script>

<style>
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
