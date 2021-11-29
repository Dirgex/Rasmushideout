<template>
<div>
    <section class="section-cta" id="cta">
      <div class="container">
        <div class="cta">
          <div class="cta-text-box">
            <h2 class="heading-secondary">Get your first meal for free!</h2>
            <p class="cta-text">
              Healthy, tasty and hassle-free meals are waiting for you. Start
              eating well today. You can cancel or pause anytime. And the first
              meal is on us!
            </p>

            <form class="cta-form" name="sign-up" netlify>
              <div>
                <label for="full-name">Full Name</label>
                <input
                  id="full-name"
                  type="text"
                  placeholder="John Smith"
                  name="full-name"
                  required
                />
              </div>

              <div>
                <label for="email">Email address</label>
                <input
                  id="email"
                  type="email"
                  placeholder="me@example.com"
                  name="email"
                  required
                />
              </div>

              <div>
                <label for="select-where">Where did you hear from us?</label>
                <select id="select-where" name="select-where" required>
                  <option value="">Please choose one option:</option>
                  <option value="friends">Friends and family</option>
                  <option value="youtube">YouTube video</option>
                  <option value="podcast">Podcast</option>
                  <option value="ad">Facebook ad</option>
                  <option value="others">Others</option>
                </select>
              </div>

              <button class="btn btn--form">Sign up now</button>

              <!-- <input type="checkbox" />
              <input type="number" /> -->
            </form>
          </div>
          <div
            class="cta-img-box"
            role="img"
            aria-label="Woman enjoying food"
          ></div>
        </div>
      </div>
    </section>
    </div>
</template>

<script>
export default {
    name: 'Contactus'
}
</script>

<style scoped>
/***************************/
/* CTA SECTION*/
/***************************/
.section-cta {
  padding: 0 0 12.8rem;
  background-color: #fdf2e9;
}

.cta {
  display: grid;
  grid-template-columns: 2fr 1fr;
  /* background-color: #e67e22; */
  box-shadow: 0 2.4rem 4.8rem rgba(0, 0, 0, 0.015);
  border-radius: 11px;
  background-image: linear-gradient(to right bottom, #eb984e, #e67e22);
  overflow: hidden;
}

.cta-text-box {
  padding: 4.8rem 6.4rem 6.4rem 4.8rem;
  color: #45260a;
}

.cta-text {
  font-size: 1.8rem;
  line-height: 1.8;
  margin-bottom: 1.8rem;
  color: #333;
}

.cta .heading-secondary {
  /* color: #45260a; */
  color: inherit;
  margin-bottom: 3.2rem;
}

.cta-img-box {

  background-size: cover;
  background-position: center;
  height: auto;
  width: auto;
}

.cta-form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: 3.2rem;
  row-gap: 2.4rem;
}

.cta-form label {
  display: block;
  font-size: 1.6rem;
  font-weight: 500;
  margin-bottom: 1.2rem;
}

.cta-form input,
.cta-form select {
  width: 100%;
  padding: 1.2rem;
  font-size: 1.8rem;
  font-family: inherit;
  color: inherit;
  border: none;
  background-color: #fdf2e9;
  border-radius: 9px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}

.cta-form input::placeholder {
  color: #aaa;
}

.cta *:focus {
  outline: none;
  box-shadow: 0 0 0 0.8rem rgba(230, 125, 34, 0.5);
}

.btn,
.btn:link,
.btn:visited {
  display: inline-block;

  font-size: 2rem;
  font-weight: 600;
  padding: 1.6rem 3.2rem;
  border-radius: 9px;
  text-decoration: none;

  /* for .btn it self */
  border: none;
  cursor: pointer;
  font-family: inherit;

  /* transition: background-color 0.3s; */
  transition: all 0.3s;
}

.btn--form {
  background-color: #45260a;
  color: #fdf2e9;
  align-self: end;
  padding: 1.2rem;
}

.btn--form:hover,
.btn--form:active {
  background-color: #fff;
  color: #555;
}

.heading-secondary {
  font-size: 4.8rem;
}
</style>