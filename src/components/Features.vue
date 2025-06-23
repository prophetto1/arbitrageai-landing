<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";

import {
  Paintbrush,
  MessageCircle,
  TabletSmartphone,
  BadgeCheck,
  Goal,
  PictureInPicture,
  MousePointerClick,
  Newspaper,
} from "lucide-vue-next";

interface FeaturesProps {
  icon: string;
  title: string;
  description: string;
}

const featureList: FeaturesProps[] = [
  {
    icon: "tabletSmartphone",
    title: "Modular Data Collectors",
    description:
      "Each exchange has its own data collector, allowing for flexible and scalable data acquisition.",
  },
  {
    icon: "badgeCheck",
    title: "Centralized Orchestration",
    description:
      "A CollectorManager orchestrates concurrent data collection from various exchanges.",
  },
  {
    icon: "goal",
    title: "Decoupled Analysis Pipeline",
    description:
      "Data is collected and stored before being analyzed in a separate, efficient pipeline.",
  },
  {
    icon: "pictureInPicture",
    title: "Pydantic Data Modeling",
    description:
      "Configuration and data modeling are handled by Pydantic for runtime validation and application robustness.",
  },
  {
    icon: "mousePointerClick",
    title: "PostgreSQL Database",
    description:
      "The project leverages PostgreSQL for reliable and scalable data storage, with support for Neon serverless databases in production.",
  },
  {
    icon: "newspaper",
    title: "Extensive Testing Suite",
    description:
      "A comprehensive testing suite, including API response validation, ensures the platform's accuracy and reliability.",
  },
];

const iconMap: Record<
  string,
  | typeof TabletSmartphone
  | typeof BadgeCheck
  | typeof Goal
  | typeof PictureInPicture
  | typeof Paintbrush
  | typeof MousePointerClick
  | typeof MessageCircle
  | typeof Newspaper
> = {
  tabletSmartphone: TabletSmartphone,
  badgeCheck: BadgeCheck,
  goal: Goal,
  pictureInPicture: PictureInPicture,
  paintbrush: Paintbrush,
  mousePointerClick: MousePointerClick,
  messageCircle: MessageCircle,
  newspaper: Newspaper,
};
</script>

<template>
  <section
    id="features"
    class="container py-24 sm:py-32 scroll-mt-40"
  >
    <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
      Features
    </h2>

    <h3 class="md:w-1/2 mx-auto text-lg text-center text-white mb-8">
      Built on a modern, asynchronous Python stack, ArbitrageAI offers a robust
      and reliable platform for identifying and analyzing arbitrage
      opportunities.
    </h3>

    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4">
      <div
        v-for="{ icon, title, description } in featureList"
        :key="title"
      >
        <Card class="h-full bg-background border-0 shadow-none">
          <CardHeader class="flex justify-center items-center">
            <div
              class="bg-primary/20 p-2 rounded-full ring-8 ring-primary/10 mb-4"
            >
              <component
                :is="iconMap[icon]"
                class="size-6 text-primary"
              />
            </div>

            <CardTitle>
              {{ title }}
            </CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground text-center">
            {{ description }}
          </CardContent>
        </Card>
      </div>
    </div>
  </section>
</template>

<style lang="less" scoped></style>
