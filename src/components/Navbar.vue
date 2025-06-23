<script lang="ts" setup>
import { ref } from "vue";

import {
  NavigationMenu,
  NavigationMenuContent,
  NavigationMenuItem,
  NavigationMenuLink,
  NavigationMenuList,
  NavigationMenuTrigger,
} from "@/components/ui/navigation-menu";
import {
  Sheet,
  SheetContent,
  SheetFooter,
  SheetHeader,
  SheetTitle,
  SheetTrigger,
} from "@/components/ui/sheet";

import { Button } from "@/components/ui/button";
import { Separator } from "@/components/ui/separator";

import { Menu } from "lucide-vue-next";
import logo from "@/assets/CI2.jpg";

interface RouteProps {
  href: string;
  label: string;
}

interface FeatureProps {
  title: string;
  description: string;
}

const routeList: RouteProps[] = [
  {
    href: "#features",
    label: "Features",
  },
  {
    href: "#how-it-works",
    label: "How It Works",
  },
  {
    href: "#contact",
    label: "Contact",
  },
  {
    href: "#faq",
    label: "FAQ",
  },
];

const featureList: FeatureProps[] = [
  {
    title: "Live Opportunity Dashboard",
    description:
      "Provides a real-time overview of active arbitrage opportunities, allowing users to quickly identify profitable trades.",
  },
  {
    title: "Detailed Opportunity Analysis",
    description:
      "Offers all necessary data for users to validate and act on a specific opportunity, including profit/loss breakdown and historical spread charts.",
  },
  {
    title: "Market Indexes",
    description:
      "A dedicated section for broader market context and sentiment indicators, such as the Crypto Fear & Greed Index.",
  },
];

const isOpen = ref<boolean>(false);
</script>

<template>
  <header
    class="shadow-dark w-full top-0 mx-auto sticky border-b z-40 grid grid-cols-3 items-center p-2 shadow-md"
    style="background-color: #1d2021"
  >
    <a
      href="/"
      class="font-bold text-lg flex items-center"
    >
      <img
        :src="logo"
        alt="ArbitrageAI logo"
        class="h-12"
      />
    </a>
    <!-- Mobile -->
    <div class="flex items-center lg:hidden">
      <Sheet v-model:open="isOpen">
        <SheetTrigger as-child>
          <Menu
            @click="isOpen = true"
            class="cursor-pointer"
          />
        </SheetTrigger>

        <SheetContent
          side="left"
          class="flex flex-col justify-between rounded-tr-2xl rounded-br-2xl bg-card"
        >
          <div>
            <SheetHeader class="mb-4 ml-4">
              <SheetTitle class="flex items-center">
                <a
                  href="/"
                  class="flex items-center"
                >
                  <img
                    :src="logo"
                    alt="ArbitrageAI logo"
                    class="h-12"
                  />
                </a>
              </SheetTitle>
            </SheetHeader>

            <div class="flex flex-col gap-2">
              <Button
                v-for="{ href, label } in routeList"
                :key="label"
                as-child
                variant="ghost"
                class="justify-start text-base"
              >
                <a
                  @click="isOpen = false"
                  :href="href"
                >
                  {{ label }}
                </a>
              </Button>
            </div>
          </div>

          <SheetFooter class="flex-col sm:flex-col justify-start items-start">
            <Separator class="mb-2" />
          </SheetFooter>
        </SheetContent>
      </Sheet>
    </div>

    <!-- Desktop -->
    <NavigationMenu class="hidden lg:block justify-self-center">
      <NavigationMenuList>
        <NavigationMenuItem>
          <NavigationMenuTrigger class="text-base">
            Features
          </NavigationMenuTrigger>
          <NavigationMenuContent>
            <div class="grid w-[600px] grid-cols-2 gap-5 p-4">
              <img
                src="https://www.radix-vue.com/logo.svg"
                alt="Beach"
                class="h-full w-full rounded-md object-cover"
              />
              <ul class="flex flex-col gap-2">
                <li
                  v-for="{ title, description } in featureList"
                  :key="title"
                  class="rounded-md p-3 text-sm hover:bg-muted"
                >
                  <p class="mb-1 font-semibold leading-none text-foreground">
                    {{ title }}
                  </p>
                  <p class="line-clamp-2 text-muted-foreground">
                    {{ description }}
                  </p>
                </li>
              </ul>
            </div>
          </NavigationMenuContent>
        </NavigationMenuItem>

        <NavigationMenuItem>
          <NavigationMenuLink asChild>
            <Button
              v-for="{ href, label } in routeList"
              :key="label"
              as-child
              variant="ghost"
              class="justify-start text-base"
            >
              <a :href="href">
                {{ label }}
              </a>
            </Button>
          </NavigationMenuLink>
        </NavigationMenuItem>
      </NavigationMenuList>
    </NavigationMenu>

    <div class="hidden lg:flex"></div>
  </header>
</template>

<style scoped>
.shadow-dark {
  box-shadow: inset 0 0 5px rgba(255, 255, 255, 0.141);
}
</style>
