<script>
  import { onMount } from "svelte";
  import Icon2 from '../../lib/images/icon.png';

  let steps = [
    {
      icon: `<svg class="w-16 h-16 text-white dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><path stroke="currentColor" stroke-width="2" d="M21 12c0 1.2-4.03 6-9 6s-9-4.8-9-6c0-1.2 4.03-6 9-6s9 4.8 9 6Z"/><path stroke="currentColor" stroke-width="2" d="M15 12a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"/></svg>`,
      des: "UEI Alliance is a collaborative group formed by various stakeholders in the energy sector, committed to global development, adoption, and compliance with the Beckn Protocol for energy-related economic transactions between digital platforms. Aimed at transforming the energy sector through the adoption of open digital protocols and interoperability standards.",
      isSvg: true,
    },
    {
      icon: Icon2,
      des: "This alliance transcends specific sectors like electric vehicles (EVs) or battery technology, encompassing a wide range of energy-related transaction domains. The alliance serves as a hub for open network concepts, providing support and advisory services. Participation from both public and private organisations is highly encouraged.",
      isSvg: false,
    },
    {
      icon: `<svg class="w-16 h-16 text-white dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24"><path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 9a3 3 0 0 1 3-3m-2 15h4m0-3c0-4.1 4-4.9 4-9A6 6 0 1 0 6 9c0 4 4 5 4 9h4Z"/></svg>`,
      des: "Its primary aim is to promote the adoption and interoperability of the Beckn Protocol within the energy field, thereby scaling the Unified Energy Interface (UEI) network. Operating as a think tank, the alliance focuses on enhancing digital economic transactions between energy platforms, particularly in resource discovery and fulfillment.",
      isSvg: true,
    }
  ];

  const animateData = async () => {
    const gsapModule = await import("gsap");
    const ScrollTriggerModule = await import("gsap/ScrollTrigger");

    const gsap = gsapModule.gsap;
    const ScrollTrigger = ScrollTriggerModule.ScrollTrigger;

    gsap.registerPlugin(ScrollTrigger);

    const tl = gsap.timeline({
      scrollTrigger: {
        trigger: ".buildAnimate",
        start: "10% 90%",
      },
    });
    tl.fromTo(
      ".buildAnimate",
      { y: 100, opacity: 0 },
      { y: 0, opacity: 1, duration: 0.5 }
    );
  };

  onMount(() => {
    animateData();
  });
</script>

<h2 class="font-bold text-4xl text-center text-transparent bg-clip-text bg-gradient-to-r from-white to-green-400 mt-10">Our Vision</h2>
<div class="w-full items-center flex flex-col justify-center">
  <div class="flex items-center w-3/4 md:w-3/4 lg:w-full justify-center lg:justify-center md:justify-center text-gray-300"></div>
</div>
<div class="w-full h-full grid grid-cols-1 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 p-5">
  {#each steps as step}
    <div class="relative buildAnimate flex flex-col bg-[#1A1F24] rounded-lg border border-gray-800 p-4">
      <div class="flex-grow flex flex-col justify-center items-center w-full bg-[#1C2428] p-4">
        <div class="flex justify-center items-center h-24">
          {#if step.isSvg}
            {@html step.icon}
          {:else}
            <img src={step.icon} alt="icon" class="h-16 w-16" />
          {/if}
        </div>
        <p class="text-md text-gray-400 mt-4">{step.des}</p>
      </div>
    </div>
  {/each}
</div>
