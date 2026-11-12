<script lang="ts">
  import mobileBg from "./assets/bg-intro-mobile.png";
  import desktopBg from "./assets/bg-intro-desktop.png";
  import errorImg from "./assets/icon-error.svg";

  let formFName = $state("");
  let formLName = $state("");
  let formEmail = $state("");
  let formPassword = $state("");

  let fNameError = $state("");
  let lNameError = $state("");
  let emailError = $state("");
  let passwordError = $state("");

  function handleSubmit(event: SubmitEvent): void {
    event.preventDefault();

    fNameError = "";
    lNameError = "";
    emailError = "";
    passwordError = "";

    if (formFName === "") {
      fNameError = "First Name cannot be empty";
    }

    if (formLName === "") {
      lNameError = "Last Name cannot be empty";
    }

    if (formEmail === "") {
      emailError = "Email cannot be empty";
    } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formEmail.trim())) {
      emailError = "Looks like this is not an email";
    }

    if (formPassword === "") {
      passwordError = "Password cannot be empty";
    }
  }
</script>

<main
  class="min-h-screen bg-red-400 bg-cover bg-center bg-no-repeat bg-[image:var(--mobile-bg)] md:bg-[image:var(--desktop-bg)]"
  style="--mobile-bg: url('{mobileBg}'); --desktop-bg: url('{desktopBg}');"
>
  <div
    class="min-h-screen flex flex-col md:flex-row justify-center gap-12 items-center max-w-6xl mx-auto py-12 text-center md:text-left"
  >
    <div class="text-white px-6">
      <h1 class="font-bold text-2xl md:text-5xl mb-4">
        Learn to code by watching others
      </h1>
      <p>
        See how experienced developers solve problems in real time. Watching
        scripted tutorials is great, but understanding how developers think is
        invaluable.
      </p>
    </div>
    <div class="px-6 w-full max-w-md">
      <div
        class=" bg-purple-700 text-white items-center text-center py-4 px-3 rounded-lg shadow-lg shadow-gray-900 mb-4"
      >
        <p><strong>Try it free 7 days</strong> then $20/mo. thereafter</p>
      </div>
      <div class="bg-white rounded-lg shadow-lg shadow-gray-900 p-3 md:p-8">
        <form
          novalidate
          onsubmit={handleSubmit}
          class="flex flex-col items-center gap-4"
        >
          <div class="relative w-full">
            <input
              class="border border-gray-300 rounded px-3 py-2 w-full"
              class:border-red-400={fNameError}
              type="text"
              name="fname"
              id="fname"
              bind:value={formFName}
              placeholder="First Name"
            />
            {#if fNameError}
              <img
                src={errorImg}
                alt="error"
                class="absolute right-3 top-1/2 -translate-y-1/2"
              />
            {/if}
          </div>
          {#if fNameError}
            <p class="text-red-400 text-xs italic self-end">{fNameError}</p>
          {/if}
          <div class="relative w-full">
            <input
              class="border border-gray-300 rounded px-3 py-2 w-full"
              class:border-red-400={lNameError}
              type="text"
              name="lname"
              id="lname"
              bind:value={formLName}
              placeholder="Last Name"
            />
            {#if lNameError}
              <img
                src={errorImg}
                alt="error"
                class="absolute right-3 top-1/2 -translate-y-1/2"
              />
            {/if}
          </div>
          {#if lNameError}
            <p class="text-red-400 text-xs italic self-end">{lNameError}</p>
          {/if}
          <div class="relative w-full">
            <input
              class="border border-gray-300 rounded px-3 py-2 w-full"
              class:border-red-400={emailError}
              type="email"
              name="email"
              id="email"
              bind:value={formEmail}
              placeholder="Email"
            />
            {#if emailError}
              <img
                src={errorImg}
                alt="error"
                class="absolute right-3 top-1/2 -translate-y-1/2"
              />
            {/if}
          </div>
          {#if emailError}
            <p class="text-red-400 text-xs italic self-end">{emailError}</p>
          {/if}
          <div class="relative w-full">
            <input
              class="border border-gray-300 rounded px-3 py-2 w-full"
              class:border-red-400={passwordError}
              type="password"
              name="password"
              id="password"
              bind:value={formPassword}
              placeholder="Password"
            />
            {#if passwordError}
              <img
                src={errorImg}
                alt="error"
                class="absolute right-3 top-1/2 -translate-y-1/2"
              />
            {/if}
          </div>
          {#if passwordError}
            <p class="text-red-400 text-xs italic self-end">
              {passwordError}
            </p>
          {/if}
          <button
            class="text-white bg-green-400 px-4 py-2 border-b-4 border-green-700 rounded w-full cursor-pointer"
            type="submit">CLAIM YOUR FREE TRIAL</button
          >
          <p class="text-gray-400 text-xs text-center">
            By clicking the button you are agreeing to our <button
              type="button"
              class="text-red-400 cursor-pointer">Terms and Services</button
            >
          </p>
        </form>
      </div>
    </div>
  </div>
</main>
