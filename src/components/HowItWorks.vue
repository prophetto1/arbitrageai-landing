<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Badge } from "@/components/ui/badge";

interface HowItWorksProps {
  badgeTitle: string;
  title: string;
  description: string;
  image: string;
}

const HowItWorksList: HowItWorksProps[] = [
  {
    badgeTitle: "Collect",
    title: "Data Collection",
    description:
      "Modular collectors gather real-time market data from various exchanges.",
    image: "roboto.png",
  },
  {
    badgeTitle: "Store",
    title: "Secure Storage",
    description:
      "Collected data is securely stored in a PostgreSQL database, with the schema defined in create_tables.sql.",
    image: "runner.png",
  },
  {
    badgeTitle: "Analyze",
    title: "Opportunity Analysis",
    description:
      "A decoupled analysis pipeline, driven by the NEFSS model, identifies and evaluates arbitrage opportunities.",
    image: "pacheco.png",
  },
  {
    badgeTitle: "Display",
    title: "Intuitive Dashboard",
    description:
      "Opportunities and market context are presented in a user-friendly, live-updating dashboard for quick insights.",
    image: "gamestation.png",
  },
];
</script>

<template>
  <section
    id="how-it-works"
    class="container py-24 sm:py-32 scroll-mt-20"
  >
    <div class="text-center mb-8">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
        How It Works
      </h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold">
        Our Step-by-Step Process
      </h2>
    </div>

    <div class="lg:w-[80%] mx-auto relative">
      <div
        v-for="(
          { badgeTitle, title, description, image }, index
        ) in HowItWorksList"
        :key="title"
        :class="[
          'flex mb-8 items-center',
          { ' flex-row-reverse': index % 2 !== 0 },
        ]"
      >
        <Card class="h-full bg-transparent border-0 shadow-none">
          <CardHeader>
            <div class="pb-4">
              <Badge>{{ badgeTitle }}</Badge>
            </div>

            <CardTitle>
              {{ title }}
            </CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground w-[80%]">
            {{ description }}
          </CardContent>
        </Card>

        <img
          :src="image"
          :alt="`Image describing ${title} `"
          className="w-[150px]  md:w-[250px] lg:w-[300px] mx-auto -scale-x-100 "
        />
        <div
          :class="[
            '-z-10 absolute right-0 w-44 h-72  lg:w-64 lg:h-80 rounded-full bg-primary/15 dark:bg-primary/10 blur-3xl',
            {
              'left-0': index % 2 !== 0,
            },
          ]"
        ></div>
      </div>
    </div>
  </section>
</template>
