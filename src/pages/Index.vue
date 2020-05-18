<template>
  <Layout>
    <form v-if="notComplete"
      name="drive-choulette"
      method="post"
      v-on:submit.prevent="handleSubmit"
      data-netlify="true"
      data-netlify-honeypot="bot-field"
    >
      <input type="hidden" name="form-name" value="drive-choulette" />
      <p hidden>
        <label> Don’t fill this out: <input name="bot-field" /> </label>
      </p>
      <div class="sender-info">
        <div>
          <label for="name" class="label" >Votre nom :</label>
          <input type="text" name="name" v-model="formData.name" required />
        </div>
        <div>
          <label for="email">Votre email :</label>
          <input type="email" name="email" v-model="formData.email" required />
        </div>
        <div>
          <label for="phone">Votre numéro de téléphone :</label>
          <input
            placeholder="ex: 0327357244"
            type="text"
            name="phone"
            v-model="formData.phone"
            required
          />
        </div>
        <div>
          <label for="enlevement">Le jour d’enlèvement :</label>
            <input type="date" name="enlevement" v-model="formData.enlevement" required />
          </div>
        </div>

      <div class="message-wrapper">
        <label for="message">Message</label>
        <textarea name="message" v-model="formData.message" required></textarea>
      </div>

      <div>
          <label for="naissance">Date de naissance :</label>
          <input type="date" max="0" name="naissance" v-model="formData.naissance" required/>
        </div>
      </div>
      <order :updatedbeers.sync="updatedbeers" />
      <button type="submit">Submit form</button>
    </form>
    <section v-else>
      <h5>
        Nous avons recu votre commande et nous vous attendons a la brasserie.
      </h5>
      <h4>16 Rue des Écoles 59111 Hordain</h4>
      <p>Pour toute questions, veuillez nous contacter au +33 3 27 35 72 44</p>
      <p>formData</p>
      <p>{{ formData }}</p>
      <p>updatedbeers</p>
      <p>{{ updatedbeers }}</p>
      <p>completeFormData</p>
      <p>{{ completeFormData }}</p>
    </section>
  </Layout>
</template>
<script>
import Order from '../components/Order'
export default {
  metaInfo: {
    title: 'Hello, world!',
  },
  components: {
    Order,
  },
  data() {
    return {
      notComplete: true,
      formData: {},
      updatedbeers: [],
    };
  },
  computed: {
    completeFormData: function() {
      const formData = this.formData;
      const updatedbeers = this.updatedbeers;
      let obj = {};
      updatedbeers.forEach((item) => {
        obj[item.nomDeLaBiere] = item.nombreDeBiere;
      });
      const completeData = { ...formData, ...obj };
      return completeData;
    },
  },
  methods: {
    encode(data) {
      return Object.keys(data)
        .map(
          (key) => encodeURIComponent(key) + '=' + encodeURIComponent(data[key])
        )
        .join('&');
    },
    handleSubmit(e) {
      fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: this.encode({
          "form-name": "drive-choulette",
          ...this.completeFormData,
        }),
      })
        .then(() => (this.notComplete = false))
        .catch((error) => alert(error));
    },
  },
};
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
