<script setup lang="ts">
import {
  Accordion,
  AccordionContent,
  AccordionItem,
  AccordionTrigger,
} from "@/components/ui/accordion";

interface FAQProps {
  question: string;
  answer: string;
  value: string;
}

const FAQList: FAQProps[] = [
  {
    question: "What is ArbitrageAI?",
    answer:
      "ArbitrageAI is a platform designed to identify cryptocurrency arbitrage opportunities, focusing on funding rate arbitrage and peer-to-peer arbitrage.",
    value: "item-1",
  },
  {
    question: "How does the funding_arbitrage service work?",
    answer:
      "The funding_arbitrage service collects data from centralized exchanges and uses the NEFSS (Net-risk-adjusted Expected Funding-fee Spread Score) model to analyze and find funding rate arbitrage opportunities.",
    value: "item-2",
  },
  {
    question: "What technologies are used in ArbitrageAI?",
    answer:
      "The project is built on an asynchronous Python stack, utilizing Pydantic for data modeling, SQLAlchemy for database interactions, and PostgreSQL as the database technology.",
    value: "item-3",
  },
  {
    question: "Where can I find the most authoritative database schema?",
    answer:
      "The most complete and authoritative database schema is always the raw SQL file: funding_arbitrage/database/migrations/create_tables.sql.",
    value: "item-4",
  },
];
</script>

<template>
  <section
    id="faq"
    class="container md:w-[700px] py-24 sm:py-32"
  >
    <div class="text-center mb-8">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider">FAQS</h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold">
        Frequently Asked Questions
      </h2>
    </div>

    <Accordion
      type="single"
      collapsible
      class="AccordionRoot"
    >
      <AccordionItem
        v-for="{ question, answer, value } in FAQList"
        :key="value"
        :value="value"
      >
        <AccordionTrigger class="text-left"> {{ question }} </AccordionTrigger>

        <AccordionContent>{{ answer }}</AccordionContent>
      </AccordionItem>
    </Accordion>

    <h3 class="font-medium mt-4">
      Still have questions?
      <a
        href="#contact"
        class="text-muted-foreground"
      >
        <a
          href="#contact"
          class="underline"
          >Contact us</a
        >
      </a>
    </h3>
  </section>
</template>
