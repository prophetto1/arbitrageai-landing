<script setup lang="ts">
import Separator from "./ui/separator/Separator.vue";
import logo from "@/assets/CI2.jpg";
</script>

<template>
  <footer
    id="footer"
    class="container py-24 pb-16 sm:py-32 sm:pb-24"
  >
    <div
      class="p-10 border rounded-2xl"
      style="background-color: #1d2021"
    >
      <div
        class="grid grid-cols-2 md:grid-cols-4 xl:grid-cols-6 gap-x-12 gap-y-8"
      >
        <div class="col-span-full xl:col-span-2">
          <a
            href="#"
            class="flex font-bold items-center"
          >
            <img
              :src="logo"
              alt="ArbitrageAI logo"
              class="h-12"
            />
          </a>
        </div>

        <div class="flex flex-col gap-2">
          <h3 class="font-bold text-lg">Contact</h3>
          <div>
            <a
              href="#"
              class="opacity-60 hover:opacity-100"
            >
              Email
            </a>
          </div>

          <div>
            <a
              href="#"
              class="opacity-60 hover:opacity-100"
            >
              Support
            </a>
          </div>
        </div>

        <div class="flex flex-col gap-2">
          <h3 class="font-bold text-lg">Platforms</h3>
          <div>
            <a
              href="#"
              class="opacity-60 hover:opacity-100"
            >
              Dashboard
            </a>
          </div>

          <div>
            <a
              href="#"
              class="opacity-60 hover:opacity-100"
            >
              Market Indexes
            </a>
          </div>
        </div>

        <div class="flex flex-col gap-2">
          <h3 class="font-bold text-lg">Help</h3>
          <div>
            <a
              href="#contact"
              class="opacity-60 hover:opacity-100"
            >
              Contact Us
            </a>
          </div>

          <div>
            <a
              href="#faq"
              class="opacity-60 hover:opacity-100"
            >
              FAQ
            </a>
          </div>

          <div>
            <a
              href="#"
              class="opacity-60 hover:opacity-100"
            >
              Documentation
            </a>
          </div>
        </div>

        <div class="flex flex-col gap-2">
          <h3 class="font-bold text-lg">Socials</h3>
          <div>
            <a
              href="#"
              class="opacity-60 hover:opacity-100"
            >
              Twitter/X
            </a>
          </div>

          <div>
            <a
              href="#"
              class="opacity-60 hover:opacity-100"
            >
              LinkedIn
            </a>
          </div>
        </div>
      </div>

      <Separator class="my-6" />
      <section className="">
        <h3 class="">
              &copy; 2025, signifAI Inc.
          <a
            target="_blank"
            href="#"
            className="text-primary transition-all border-primary hover:border-b-2"
          </a>
        </h3>
      </section>
    </div>
  </footer>
</template>
