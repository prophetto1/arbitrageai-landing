<script setup lang="ts">
import {
  Card,
  CardDescription,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";

import { Badge } from "@/components/ui/badge";

enum ProService {
  YES = 1,
  NO = 0,
}

interface ServiceProps {
  title: string;
  pro: ProService;
  description: string;
}

const serviceList: ServiceProps[] = [
  {
    title: "Funding Rate Arbitrage",
    description:
      "Identifies arbitrage opportunities based on funding rates across centralized exchanges.",
    pro: 0,
  },
  {
    title: "Peer-to-Peer (P2P) Arbitrage",
    description:
      "A secondary service focused on finding opportunities in peer-to-peer cryptocurrency markets.",
    pro: 0,
  },
  {
    title: "Real-time Data Collection",
    description:
      "Utilizes asyncio and httpx for concurrent, asynchronous API calls to collect real-time market data.",
    pro: 0,
  },
  {
    title: "NEFSS Model Analysis",
    description:
      "Core logic centered around the Net-risk-adjusted Expected Funding-fee Spread Score (NEFSS) model for opportunity assessment.",
    pro: 1,
  },
];
</script>

<template>
  <section
    id="services"
    class="container py-24 sm:py-32 scroll-mt-20"
  >
    <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
      Services
    </h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
      Our Core Services
    </h2>
    <h3 class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground mb-8">
      ArbitrageAI offers two primary services to cater to different arbitrage
      strategies.
    </h3>
    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4"></div>

    <div
      class="grid sm:grid-cols-2 lg:grid-cols-2 gap-4 w-full lg:w-[60%] mx-auto"
    >
      <div
        v-for="{ title, description, pro } in serviceList"
        :key="title"
      >
        <Card class="bg-muted/60 dark:bg-card h-full relative">
          <CardHeader>
            <CardTitle>{{ title }}</CardTitle>
            <CardDescription>{{ description }}</CardDescription>
          </CardHeader>
          <Badge
            v-if="pro === ProService.YES"
            variant="secondary"
            class="absolute -top-2 -right-3"
            >PRO</Badge
          >
        </Card>
      </div>
    </div>
  </section>
</template>
