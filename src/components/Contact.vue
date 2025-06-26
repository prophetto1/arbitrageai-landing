<script setup lang="ts">
import { ref, reactive } from "vue";
import { Button } from "./ui/button";
import { Card, CardHeader, CardContent, CardFooter } from "./ui/card";
import { Label } from "./ui/label";
import { Input } from "./ui/input";
import {
  Select,
  SelectContent,
  SelectGroup,
  SelectItem,
  SelectTrigger,
  SelectValue,
} from "./ui/select";
import { Textarea } from "./ui/textarea";
import { Alert, AlertDescription, AlertTitle } from "@/components/ui/alert";

import { AlertCircle, Mail, CheckCircle, Loader2 } from "lucide-vue-next";

interface ContactFormProps {
  firstName: string;
  lastName: string;
  email: string;
  subject: string;
  message: string;
}

const contactForm = reactive<ContactFormProps>({
  firstName: "",
  lastName: "",
  email: "",
  subject: "General Inquiry",
  message: "",
});

const isSubmitting = ref<boolean>(false);
const submitStatus = ref<'idle' | 'success' | 'error'>('idle');
const errorMessage = ref<string>('');

// EmailJS configuration - You'll need to replace these with your actual values
const EMAILJS_SERVICE_ID = 'your_service_id';
const EMAILJS_TEMPLATE_ID = 'your_template_id';
const EMAILJS_PUBLIC_KEY = 'your_public_key';

const validateForm = (): boolean => {
  const { firstName, lastName, email, subject, message } = contactForm;
  
  if (!firstName.trim() || !lastName.trim() || !email.trim() || !message.trim()) {
    errorMessage.value = 'Please fill in all required fields.';
    return false;
  }
  
  // Basic email validation
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (!emailRegex.test(email)) {
    errorMessage.value = 'Please enter a valid email address.';
    return false;
  }
  
  return true;
};

const resetForm = () => {
  contactForm.firstName = '';
  contactForm.lastName = '';
  contactForm.email = '';
  contactForm.subject = 'General Inquiry';
  contactForm.message = '';
};

const handleSubmit = async () => {
  // Reset previous states
  submitStatus.value = 'idle';
  errorMessage.value = '';
  
  // Validate form
  if (!validateForm()) {
    submitStatus.value = 'error';
    return;
  }
  
  isSubmitting.value = true;
  
  try {
    // Dynamic import of EmailJS to avoid build issues if not installed
    const emailjs = await import('@emailjs/browser');
    
    // Prepare template parameters
    const templateParams = {
      from_name: `${contactForm.firstName} ${contactForm.lastName}`,
      from_email: contactForm.email,
      subject: contactForm.subject,
      message: contactForm.message,
      to_name: 'ArbitrageAI Team',
    };
    
    // Send email via EmailJS
    await emailjs.send(
      EMAILJS_SERVICE_ID,
      EMAILJS_TEMPLATE_ID,
      templateParams,
      EMAILJS_PUBLIC_KEY
    );
    
    submitStatus.value = 'success';
    resetForm();
    
    // Auto-hide success message after 5 seconds
    setTimeout(() => {
      submitStatus.value = 'idle';
    }, 5000);
    
  } catch (error) {
    console.error('EmailJS Error:', error);
    submitStatus.value = 'error';
    errorMessage.value = 'Failed to send message. Please try again or contact us directly.';
  } finally {
    isSubmitting.value = false;
  }
};
</script>

<template>
  <section
    id="contact"
    class="container py-24 sm:py-32 scroll-mt-20"
  >
    <section class="grid grid-cols-1 md:grid-cols-2 gap-8">
      <div>
        <div class="mb-4">
          <h2 class="text-lg text-primary mb-2 tracking-wider">Contact</h2>
          <h2 class="text-3xl md:text-4xl font-bold">Connect With Us</h2>
        </div>
        <p class="mb-8 text-muted-foreground lg:w-5/6">
          Have questions about ArbitrageAI? Want to learn more about our platform? 
          Reach out to us and we'll get back to you within 24 hours.
        </p>

        <div class="flex flex-col gap-4">
          <div>
            <div class="flex gap-2 mb-1">
              <Mail />
              <div class="font-bold">Email Us Directly</div>
            </div>
            <p class="text-muted-foreground ml-8">
              support@arbitrageai.com
            </p>
          </div>
        </div>
      </div>

      <!-- form -->
      <Card class="bg-muted/60 dark:bg-card">
        <CardHeader class="text-primary text-2xl">
          <h3 class="text-xl font-semibold">Send us a message</h3>
        </CardHeader>
        <CardContent>
          <form
            @submit.prevent="handleSubmit"
            class="grid gap-4"
          >
            <div class="flex flex-col md:flex-row gap-4">
              <div class="flex flex-col w-full gap-1.5">
                <Label for="first-name">First Name *</Label>
                <Input
                  id="first-name"
                  type="text"
                  v-model="contactForm.firstName"
                  autocomplete="given-name"
                  :disabled="isSubmitting"
                  required
                />
              </div>

              <div class="flex flex-col w-full gap-1.5">
                <Label for="last-name">Last Name *</Label>
                <Input
                  id="last-name"
                  type="text"
                  v-model="contactForm.lastName"
                  autocomplete="family-name"
                  :disabled="isSubmitting"
                  required
                />
              </div>
            </div>

            <div class="flex flex-col gap-1.5">
              <Label for="email">Email *</Label>
              <Input
                id="email"
                type="email"
                v-model="contactForm.email"
                autocomplete="email"
                :disabled="isSubmitting"
                required
              />
            </div>

            <div class="flex flex-col gap-1.5">
              <Label for="subject">Subject</Label>
              <Select v-model="contactForm.subject" :disabled="isSubmitting">
                <SelectTrigger>
                  <SelectValue placeholder="Select a subject" />
                </SelectTrigger>
                <SelectContent>
                  <SelectGroup>
                    <SelectItem value="General Inquiry">
                      General Inquiry
                    </SelectItem>
                    <SelectItem value="Platform Demo">
                      Platform Demo
                    </SelectItem>
                    <SelectItem value="Technical Support">
                      Technical Support
                    </SelectItem>
                    <SelectItem value="Partnership">
                      Partnership
                    </SelectItem>
                    <SelectItem value="Investment Inquiry">
                      Investment Inquiry
                    </SelectItem>
                  </SelectGroup>
                </SelectContent>
              </Select>
            </div>

            <div class="flex flex-col gap-1.5">
              <Label for="message">Message *</Label>
              <Textarea
                id="message"
                rows="5"
                v-model="contactForm.message"
                :disabled="isSubmitting"
                placeholder="Tell us about your interest in ArbitrageAI..."
                required
              />
            </div>

            <!-- Success Message -->
            <Alert
              v-if="submitStatus === 'success'"
              class="border-green-200 bg-green-50 dark:bg-green-950"
            >
              <CheckCircle class="w-4 h-4 text-green-600" />
              <AlertTitle class="text-green-800 dark:text-green-200">Success!</AlertTitle>
              <AlertDescription class="text-green-700 dark:text-green-300">
                Your message has been sent successfully. We'll get back to you within 24 hours.
              </AlertDescription>
            </Alert>

            <!-- Error Message -->
            <Alert
              v-if="submitStatus === 'error'"
              variant="destructive"
            >
              <AlertCircle class="w-4 h-4" />
              <AlertTitle>Error</AlertTitle>
              <AlertDescription>
                {{ errorMessage }}
              </AlertDescription>
            </Alert>

            <Button 
              type="submit" 
              class="mt-4" 
              :disabled="isSubmitting"
            >
              <Loader2 
                v-if="isSubmitting" 
                class="w-4 h-4 mr-2 animate-spin" 
              />
              {{ isSubmitting ? 'Sending...' : 'Send Message' }}
            </Button>
          </form>
        </CardContent>

        <CardFooter></CardFooter>
      </Card>
    </section>
  </section>
</template>
