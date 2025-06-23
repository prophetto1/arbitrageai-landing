<script lang="ts" setup>
import { ref, computed } from "vue";

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
  { href: "#features", label: "Features" },
  { href: "#services", label: "Services" },
  { href: "#contact", label: "Contact" },
  { href: "#team", label: "About" },
  { href: "#faq", label: "FAQ" },
];

const desktopRouteList = computed(() =>
  routeList.filter((route) => route.label !== "Features")
);

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
    class="shadow-dark w-full top-0 sticky border-b z-40 grid grid-cols-2 lg:grid-cols-3 items-center p-2 shadow-md"
    style="background-color: #1d2021"
  >
    <a
      href="/"
      class="font-bold text-lg flex items-center"
    >
      <img
        :src="logo"
        alt="ArbitrageAI logo"
        class="h-12 mr-2 rounded"
      />
    </a>
    <!-- Mobile -->
    <div class="flex items-center justify-self-end lg:hidden">
      <Sheet v-model:open="isOpen">
        <SheetTrigger as-child>
          <Menu @click="isOpen = true" class="cursor-pointer" />
        </SheetTrigger>
        <SheetContent
          side="left"
          class="flex flex-col justify-between rounded-tr-2xl rounded-br-2xl bg-card"
        >
          <div>
            <SheetHeader class="mb-4 ml-4">
              <SheetTitle class="flex items-center">
                <img :src="logo" alt="ArbitrageAI logo" class="h-11 mr-2" />
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
                <a @click="isOpen = false" :href="href">{{ label }}</a>
              </Button>
            </div>
          </div>
          <SheetFooter class="flex-col items-start">
            <Separator class="mb-2" />
          </SheetFooter>
        </SheetContent>
      </Sheet>
    </div>
    <!-- Desktop -->
    <NavigationMenu class="hidden lg:block justify-self-center">
      <NavigationMenuList>
        <NavigationMenuItem
          v-for="{ href, label } in routeList"
          :key="label"
        >
          <NavigationMenuLink asChild>
            <Button
              as-child
              variant="ghost"
              class="text-base"
            >
              <a :href="href">
                {{ label }}
              </a>
            </Button>
          </NavigationMenuLink>
        </NavigationMenuItem>
      </NavigationMenuList>
    </NavigationMenu>
    <div class="hidden lg:flex lg:justify-self-end"></div>
  </header>
</template>

<style scoped>
.shadow-dark {
  box-shadow: inset 0 0 5 rgba(255, 255, 255, 0.141);
}
</style>
