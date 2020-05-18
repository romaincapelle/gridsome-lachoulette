<template>
  <Layout>
    <form
      name="contact"
      method="post"
      v-on:submit.prevent="handleSubmit"
      action="/success/"
      data-netlify="true"
      data-netlify-honeypot="bot-field"
    >
      <input type="hidden" name="form-name" value="contact" />
      <p hidden>
        <label> Don’t fill this out: <input name="bot-field" /> </label>
      </p>
      <div class="sender-info">
        <div>
          <label for="name" class="label">Votre nom :</label>
          <input type="text" name="name" v-model="formData.name" />
        </div>
        <div>
          <label for="email">Votre email :</label>
          <input type="email" name="email" v-model="formData.email" />
        </div>
        <div>
          <label for="phone">Votre numéro de téléphone :</label>
          <input
            placeholder="ex: 0327357244"
            type="text"
            name="phone"
            v-model="formData.phone"
          />
        </div>
        <div>
          <label for="enlevement">Le jour d’enlèvement :</label>
            <input type="date" name="enlevement" v-model="formData.enlevement" />
          </div>
        </div>

      <div class="message-wrapper">
        <label for="message">Message</label>
        <textarea name="message" v-model="formData.message"></textarea>
      </div>

      <div>
          <label for="naissance">Date de naissance :</label>
          <input type="date" max="0" name="naissance" v-model="formData.naissance" />
        </div>
      </div>

      <button type="submit">Submit form</button>
    </form>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!',
  },
  data() {
    return {
      formData: {},
    };
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
          'form-name': e.target.getAttribute('name'),
          ...this.formData,
        }),
      })
        .then(() => this.$router.push('/About'))
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
