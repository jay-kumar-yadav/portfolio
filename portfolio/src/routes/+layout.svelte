<script>
  import Footer from "../components/Footer.svelte";
  import Header from "../components/Header.svelte";
  import "../app.css";

  let y = 0;
  let innerWidth = 0;
  let innerHeight = 0;

  function goTop() {
    window.scrollTo({ top: 0, behavior: "smooth" });
  }
</script>

<div class="container relative flex flex-col max-w-[1400px] mx-auto w-full text-sm sm:text-base min-h-screen">
  <!-- Scroll-to-top button -->
  <div
    class={"fixed bottom-0 w-full duration-200 flex p-10 z-[10] " +
      (y > 0 ? "opacity-100 pointer-events-auto" : "pointer-events-none opacity-0")}
  >
  <button
  on:click={goTop}
  class="ml-auto rounded-full bg-slate-900 text-violet-400 p-3 sm:p-4 hover:bg-slate-800 cursor-pointer grid place-items-center"
  aria-label="Scroll to top"
>
  <i class="fa-solid fa-arrow-up"></i>
</button>

  </div>

  
  <Header {y} {innerHeight} />

  <!-- Slot for content -->
  <slot />

  <!-- Footer component -->
  <Footer />
</div>

<!-- Bind window properties -->
<svelte:window bind:scrollY={y} bind:innerHeight bind:innerWidth />
