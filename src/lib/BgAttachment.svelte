<script lang="ts">
  import gsap from "gsap";
  import ScrollTrigger from "gsap/ScrollTrigger";
  import { onMount } from "svelte";

  import cat from "../assets/s1200.png?url";

  let container: HTMLElement | null, fadeContainer: HTMLElement | null;

  onMount(() => {
    gsap.registerPlugin(ScrollTrigger);
    if (container) {
      ScrollTrigger.create({
        trigger: container,
        start: "top bottom",
        end: "bottom top",
        markers: true,
        onUpdate: () => {
          if (container) {
            const innerHeight = window.innerHeight; // количество пикселей вьюпорта по высоте
            const scrollY = self.scrollY; // кол-во пикселей, на которые проскроллил пользователь
            const offsetTop = container.offsetTop; // количество пикселей от самого начала страницы до начала блока
            const offsetHeight = container.offsetHeight; // количество пикселей, которое занимает блок по высоте

            const containerTop = scrollY - offsetTop; // пока меньше 0, начало блока находится ниже верха страницы. когда > 0, начало блока уезжает вверх за вьюпорт
            const containerBottom =
              scrollY + innerHeight - (offsetTop + offsetHeight); // пока меньше 0, не виден. когда > 0, начинаем его видеть
            console.log(containerTop, containerBottom);

            let maskTopPosition = -100,
              maskBottomPosition = 100;

            if (containerTop > 0) {
              // блок достиг верха вьюпорта - видим верхнюю маску
              maskTopPosition = containerTop;

              if (containerBottom < 0) {
                // середина блока - должны быть две маски сверху и снизу
                maskBottomPosition =
                  innerHeight - offsetHeight + (scrollY - offsetTop);
              } else {
                // видна только маска сверху
                maskTopPosition = containerTop;
                maskBottomPosition = 200;
              }
            } else {
              // видна только маска снизу
              maskTopPosition = -200;
              maskBottomPosition =
                innerHeight - offsetHeight + (scrollY - offsetTop);
            }

            if (fadeContainer) {
              fadeContainer.style.maskPosition = `center ${maskTopPosition.toString()}px, center ${maskBottomPosition.toString()}px`;
            }
          }
        },
      });
    }
  });
</script>

<div class="wrap" bind:this={container}>
  <div class="image">
    <img src={cat} alt="" />
  </div>
  <div class="text" bind:this={fadeContainer}>
    <h2 class="title">Test title</h2>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <h2 class="title">Test title</h2>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
    <div>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos
      aperiam quaerat, earum sunt amet ipsa quisquam harum exercitationem
      repellat maxime veritatis consequuntur inventore iste nostrum mollitia,
      facilis voluptatem voluptas!
    </div>
  </div>
</div>

<div class="another-wrap">
  <div>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos aperiam
    quaerat, earum sunt amet ipsa quisquam harum exercitationem repellat maxime
    veritatis consequuntur inventore iste nostrum mollitia, facilis voluptatem
    voluptas!
  </div>
  <div>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos aperiam
    quaerat, earum sunt amet ipsa quisquam harum exercitationem repellat maxime
    veritatis consequuntur inventore iste nostrum mollitia, facilis voluptatem
    voluptas!
  </div>
  <div>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos aperiam
    quaerat, earum sunt amet ipsa quisquam harum exercitationem repellat maxime
    veritatis consequuntur inventore iste nostrum mollitia, facilis voluptatem
    voluptas!
  </div>
  <div>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos aperiam
    quaerat, earum sunt amet ipsa quisquam harum exercitationem repellat maxime
    veritatis consequuntur inventore iste nostrum mollitia, facilis voluptatem
    voluptas!
  </div>
  <div>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos aperiam
    quaerat, earum sunt amet ipsa quisquam harum exercitationem repellat maxime
    veritatis consequuntur inventore iste nostrum mollitia, facilis voluptatem
    voluptas!
  </div>
  <div>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos aperiam
    quaerat, earum sunt amet ipsa quisquam harum exercitationem repellat maxime
    veritatis consequuntur inventore iste nostrum mollitia, facilis voluptatem
    voluptas!
  </div>
</div>

<style lang="scss">
  .wrap {
    display: flex;
    position: relative;
  }

  .text {
    padding: 50px 0;
    mask-image:
      linear-gradient(to bottom, transparent 50px, #fff 200px, #fff 100%),
      // маска снизу
      linear-gradient(
          to bottom,
          #fff 0%,
          #fff calc(100% - 200px),
          transparent calc(100% - 50px)
        );
    mask-size: 100%, 100%;
    mask-repeat: no-repeat, no-repeat;
    mask-position:
      center -200px,
      center 0;
    mask-composite: intersect;
  }

  .title {
    width: fit-content;
    margin: 30px auto;
    background: linear-gradient(to right, red 0, purple 100%);
    background-clip: text;
    color: transparent;
  }

  img {
    width: 300px;
    height: auto;
    position: sticky;
    top: 20%;
  }

  .another-wrap {
    margin-top: 100px;
    background: yellowgreen;
  }
</style>
