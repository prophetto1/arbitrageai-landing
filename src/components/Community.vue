<script setup lang="ts">
import {
  Card,
  CardHeader,
  CardTitle,
  CardFooter,
  CardContent,
} from "@/components/ui/card";

import { Button } from "@/components/ui/button";

import DiscordIcon from "@/icons/DiscordIcon.vue";
</script>

<template>
  <section
    id="community"
    class="py-12 scroll-mt-20"
  >
    <hr />
    <div class="container py-20 sm:py-20">
      <div class="lg:w-[60%] mx-auto">
        <Card
          class="bg-background shadow-none text-center flex flex-col items-center justify-center border-0"
        >
          <CardHeader>
            <CardTitle class="text-4xl md:text-5xl font-bold">
              <Component
                class="w-20 h-20 m-auto mb-4"
                :is="DiscordIcon"
              />
              Join 3,000+
              <span
                class="text-transparent bg-gradient-to-r from-[#D247BF] to-primary bg-clip-text"
              >
                Profitable Traders
              </span>
            </CardTitle>
          </CardHeader>
          <CardContent class="lg:w-[80%] text-xl text-muted-foreground">
            Be part of the fastest-growing arbitrage community in crypto. Get exclusive access to private Discord with real-time opportunity alerts, weekly strategy sessions with $100k+ earners, early access to new exchange integrations, and custom bot development for your strategies.
          </CardContent>

          <CardFooter>
            <Button as-child>
              <a
                href="#"
                target="_blank"
              >
                Join Our Community
              </a>
            </Button>
          </CardFooter>
        </Card>
      </div>
    </div>
    <hr />
  </section>
</template>
