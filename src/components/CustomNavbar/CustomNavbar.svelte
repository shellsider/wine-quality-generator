<script>
  import {
    Navbar,
    NavBrand,
    NavLi,
    NavUl,
    NavHamburger,
    ImagePlaceholder,
    Skeleton,
    TextPlaceholder,
  } from "flowbite-svelte";
</script>

<div class="relative px-8">
  <Navbar
    let:NavContainer
    color="primary"
    class="px-2 sm:px-4 py-2.5 fixed w-full z-20 top-0 start-0 border-b"
  >
    <NavBrand href="/">
      <img
        src="src\assets\imageHomeBig.png"
        class="me-3 h-6 sm:h-9"
        alt="Flowbite Logo"
      />
      <span
        class="self-center whitespace-nowrap text-xl font-semibold dark:text-white"
        >Flowbite</span
      >
    </NavBrand>
    <NavHamburger />
    <NavUl>
      <NavLi href="/" active={true}>Home</NavLi>
    </NavUl>
  </Navbar>
</div>
