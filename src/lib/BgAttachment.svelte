<script lang="ts">
  import gsap from "gsap";
  import ScrollTrigger from "gsap/ScrollTrigger";
  import { onMount } from "svelte";

  let container: HTMLElement | null = null;

  onMount(() => {
    if (container) {
      console.log(container);
    }

    gsap.registerPlugin(ScrollTrigger);
    gsap.to(container, {
      scrollTrigger: {
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

            let maskTopPosition = -200,
              maskBottomPosition = 200;

            // maskTopPosition = containerTop > 0 ? containerTop : -200;
            // maskBottomPosition =
            //   (containerTop > 0 && containerBottom < 0) || containerTop < 0
            //     ? (maskBottomPosition =
            //         window.innerHeight - container.offsetHeight)
            //     : 200;

            if (containerTop > 0) {
              // блок достиг верха вьюпорта - видим верхнюю маску
              maskTopPosition = containerTop;

              if (containerBottom < 0) {
                // блок достиг верха вьюпорта, но конец блока не виден - мы в середине - должны быть две маски сверху и снизу
                maskBottomPosition =
                  innerHeight - offsetHeight + (scrollY - offsetTop);
              } else {
                // видим нижнюю границу блока - видна только одна маска сверху
                maskTopPosition = containerTop;
                maskBottomPosition = 200;
              }
            } else {
              // видна только маска снизу, мы находимся выше блока
              maskTopPosition = -200;
              maskBottomPosition =
                innerHeight - offsetHeight + (scrollY - offsetTop);
            }

            container.style.maskPosition = `center ${maskTopPosition.toString()}px, center ${maskBottomPosition.toString()}px`;
          }
        },
      },
    });
  });
</script>

<div class="wrap" bind:this={container}>
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
  <div>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magni quos aperiam
    quaerat, earum sunt amet ipsa quisquam harum exercitationem repellat maxime
    veritatis consequuntur inventore iste nostrum mollitia, facilis voluptatem
    voluptas!
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
    padding: 100px 0;
    // маска сверху
    mask-image:
      linear-gradient(to bottom, transparent 0, #fff 200px, #fff 100%),
      // маска снизу
      linear-gradient(
          to bottom,
          #fff 0%,
          #fff calc(100% - 200px),
          transparent 100%
        );
    mask-size: 100%, 100%;
    mask-repeat: no-repeat, no-repeat;
    mask-position:
      center -200px,
      center 0;
    mask-composite: intersect;
    // background-image: linear-gradient(to right, purple 0, blue 100%), linear-gradient(to left, pink 0, red 100%);
    // background-size: 100% 40px, 100% 40px;
    // background-repeat: no-repeat, no-repeat;
    // background-attachment: fixed, fixed;
    // background-position: top center, bottom center;

    // max-height: 200px;
    // overflow: auto;

    transition: 0.3s ease-in-out;
    transition-property: mask-position;
  }

  .another-wrap {
    margin-top: 100px;
    background: yellowgreen;
  }
</style>
