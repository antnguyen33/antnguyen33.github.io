<script>
  import { isSidebarOpen } from "$lib/stores";
  import clickOutside from "$lib/utils/clickOutside";
  import Swipe from "$lib/components/Swipe.svelte";

  const handleClickOutside = () => {
    if ($isSidebarOpen) {
      $isSidebarOpen = false;
      direction = "";
    }
  };

  let direction;

  $: if (direction == "right") {
    $isSidebarOpen = true;
  } else if (direction == "left") {
    $isSidebarOpen = false;
  }
</script>

<div
  class="sidebar-toggle"
  use:clickOutside
  on:click_outside={handleClickOutside}
>
  <label for="check">
    <input type="checkbox" id="check" bind:checked={$isSidebarOpen} />
    <span />
    <span />
    <span />
  </label>
</div>
<Swipe bind:direction />

<style>
  .sidebar-toggle {
    position: absolute;
    display: inline-block;
    margin: 0.5rem 2rem;
  }
  label {
    display: flex;
    flex-direction: column;
    width: 40px;
    cursor: pointer;
  }

  label span {
    background: var(--text-light);
    border-radius: 5px;
    height: 3px;
    margin: 5px 0;
    transition: 0.4s cubic-bezier(0.68, -0.6, 0.32, 1.6);
  }

  span:nth-of-type(1) {
    width: 50%;
  }

  span:nth-of-type(2) {
    width: 100%;
  }

  span:nth-of-type(3) {
    width: 75%;
  }

  input[type="checkbox"] {
    display: none;
  }
  input[type="checkbox"]:checked ~ span {
    color: white;
  }

  input[type="checkbox"]:checked ~ span:nth-of-type(1) {
    transform-origin: bottom;
    transform: rotatez(45deg) translate(6px, 2px);
  }

  input[type="checkbox"]:checked ~ span:nth-of-type(2) {
    transform-origin: top;
    transform: rotatez(-45deg);
  }

  input[type="checkbox"]:checked ~ span:nth-of-type(3) {
    transform-origin: bottom;
    width: 50%;
    transform: translate(17px, -6px) rotatez(45deg);
  }

  @media screen and (max-width: 800px) {
    .sidebar-toggle {
      margin: 1.5rem;
    }
    label {
      width: 32px;
    }

    label span {
      height: 2px;
      margin: 3px 0;
    }

    input[type="checkbox"]:checked ~ span:nth-of-type(1) {
      transform: rotatez(45deg) translate(4px, 0px);
    }
    input[type="checkbox"]:checked ~ span:nth-of-type(3) {
      transform: translate(13px, -3px) rotatez(45deg);
    }
  }
</style>
