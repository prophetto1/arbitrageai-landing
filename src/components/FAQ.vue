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
      "ArbitrageAI is the first platform to combine funding rate arbitrage with P2P market inefficiencies, creating multiple revenue streams from a single dashboard.",
    value: "item-1",
  },
  {
    question: "How much can I realistically earn?",
    answer:
      "Our users typically see 15-30% annual returns. Top performers using both funding and P2P arbitrage have achieved 40-50% APY.",
    value: "item-2",
  },
  {
    question: "What's the minimum investment?",
    answer:
      "Start with as little as $1,000. Our smart position sizing ensures you can participate in opportunities regardless of capital size.",
    value: "item-3",
  },
  {
    question: "How does P2P arbitrage work?",
    answer:
      "We scan thousands of P2P advertisements across platforms like Binance P2P, LocalBitcoins, and Paxful. When the same asset trades at different prices due to payment methods or merchant factors, you profit from the spread.",
    value: "item-4",
  },
  {
    question: "Is this actually risk-free?",
    answer:
      "While no investment is 100% risk-free, our strategies are market-neutral. You're not betting on price direction - you're capturing inefficiencies that exist due to market structure.",
    value: "item-5",
  },
];
</script>

<template>
  <section
    id="faq"
    class="container md:w-[700px] py-24 sm:py-32 scroll-mt-24"
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
