<template>
    <div class="container">
        <form>
          <label>From</label>
          <input 
            type="text" 
            v-model="name"
            name="name"
            placeholder="Name"
          >
          <label>To</label>
          <input 
            type="email" 
            v-model="email"
            name="email"
            placeholder="Email"
            >
          <label>Message</label>
          <textarea 
            name="message"
            v-model="message"
            cols="30" rows="5"
            placeholder="Message">
          </textarea>
          
          <input type="submit" value="Request Extension">
        </form>
    </div>
</template>

<script>
import emailjs from 'emailjs-com';
export default {
  name: 'ContactUs',
  data() {
    return {
      name: '',
      email: '',
      message: ''
    }
  },
  methods: {
    sendEmail(e) {
      try {
        emailjs.sendForm('service_wac2td7', 'template_o15678q', e.target, 'eWajQLxcfv4t182KTH7vm', {
          name: this.name,
          email: this.email,
          message: this.meessage
        })
      } catch (error) {
          alert({error})
      }
    //   this.name = ''
    //   this.email = ''
    //   this.message = ''
    },
  }
}
</script>


<style scoped>
* {box-sizing: border-box;}

.container {
  display: block;
  margin:auto;
  text-align: center;
  border-radius: 5px;
  background-color: #47a4fb;
  padding: 20px;
  width: 40%;
}

label {
  float: left;
  color: white;
}

input[type=text], [type=email], textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

input[type=submit] {
  background-color: #397ebf;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #3a89d3;
}
</style>