<script setup>
import { ref, reactive } from 'vue'

// ---- Contact details (from your previous message) ----
const phoneNumber = '+1 646-294-6127'
const phoneNumberTel = '+16462946127'
const email = 'kkprayerchapel@gmail.com'
const officeHours = '9:00am - 5:00pm, Monday - Friday'
const officeLocation = [' 1200 W Speedway Blvd , Tucson, AZ, United States, 85745', 'Oro Valley, AZ · Marana, AZ · Tucson, AZ · Sahuarita, AZ']

// ---- Social links (matching the Navbar) ----
const socials = [
  { name: 'Facebook',  url: 'https://www.facebook.com/yourpage',     key: 'facebook' },
  { name: 'WhatsApp',  url: 'https://wa.me/16462946127',             key: 'whatsapp' },
  { name: 'YouTube',   url: 'https://www.youtube.com/@yourchannel',  key: 'youtube' },
  { name: 'Instagram', url: 'https://www.instagram.com/yourpage',    key: 'instagram' },
  { name: 'TikTok',    url: 'https://www.tiktok.com/@yourpage',      key: 'tiktok' },
]

// ---- Inquiry type options (from Bethel) ----
const inquiryTypes = [
  'General',
  'Arise & Build',
  'Bethel Music',
  'BSSM',
  'Conferences & Events',
  'Giving',
  'Online Store',
  'Press Inquiry',
  'Testimony',
]

// ---- Form state ----
const form = reactive({
  inquiryType: '',
  name: '',
  email: '',
  subject: '',
  message: '',
})

const submitted = ref(false)
const errors = ref({})

const validate = () => {
  const e = {}
  if (!form.inquiryType) e.inquiryType = 'Please select an inquiry type.'
  if (!form.name.trim()) e.name = 'Name is required.'
  if (!form.email.trim()) e.email = 'Email is required.'
  else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)) e.email = 'Enter a valid email.'
  if (!form.subject.trim()) e.subject = 'Subject is required.'
  if (!form.message.trim()) e.message = 'Message is required.'
  errors.value = e
  return Object.keys(e).length === 0
}

const submitForm = () => {
  if (!validate()) return
  // Replace with your API call / email service (e.g. EmailJS, Formspree, backend endpoint)
  console.log('Form submitted:', { ...form })
  submitted.value = true
  // Reset form
  Object.keys(form).forEach((k) => (form[k] = ''))
  setTimeout(() => (submitted.value = false), 6000)
}

// ---- FAQ accordion (10 items verbatim from Bethel) ----
const openFaq = ref(null)
const toggleFaq = (index) => {
  openFaq.value = openFaq.value === index ? null : index
}

const faqs = [
  {
    q: 'Are your offering readings available online?',
    a: 'Yes, you can view our offering readings on our Offering Readings page.',
  },
  {
    q: 'Do you offer hearing devices or have someone who signs for the hearing impaired?',
    a: 'We do not offer ASL interpretation or listening devices at this time.',
  },
  {
    q: 'Do you translate messages into different languages?',
    a: 'You can download our Sermon of the Week podcast in eight different languages each week. We may be able to translate messages live during our larger conferences and events. To arrange this, please email us after registering for an event.',
  },
  {
    q: 'How can I request a speaker to come to my church?',
    a: 'Request a speaker on our Itineraries page. It\'s also where many of our speaker itineraries are posted — a great place to find out if someone\'s coming to a church near you!',
  },
  {
    q: 'How can I submit a prayer request?',
    a: 'We have pastors who can pray with you over the phone or in our offices Monday - Friday from 9:00am - 12:00pm and 1:00pm - 4:00pm (PST). Simply call us. We\'d love to chat with you. If you want prayer for physical healing, our Healing Rooms teams are available online and in person on Saturdays.',
  },
  {
    q: 'How can I visit the Healing Rooms?',
    a: 'Currently, we invite you to join us on our Healing Rooms Facebook Page to enjoy the Encounter Room online Saturday mornings from 9:00 - 11:00am. Our Healing Rooms Online Zoom Ministry is available Saturday mornings from 9:00 - 10:00am PST by appointment only. Please pre-register to join us.',
  },
  {
    q: 'I\'ve lost an item, how do I find it?',
    a: 'Looking for an item you lost while visiting? Please fill out the form below, and our team will see if your item has been found! If you lost an item while at a conference, please be sure to visit the Info Table first.',
  },
  {
    q: 'What are your office hours?',
    a: 'Our administrative offices are open Monday - Friday, 9:00am - 5:00pm.',
  },
  {
    q: 'What times are your services?',
    a: 'We have multiple services. For a full listing of all weekend services at our campuses, see our Weekends page. We recommend attending our 8:00am or 1:00pm service for easier parking and more seating.',
  },
  {
    q: 'Where can I stay during my visit?',
    a: 'We do not offer accommodations, but we\'d still love to help you find a place to stay! We\'ve put together a list of places to stay on our Accommodations page.',
  },
]

// ---- Footer link columns ----
const footerColumns = [
  {
    title: 'Connect',
    links: ['Weekends', 'Get Involved', 'Calendar', 'Featured Events', 'Schools', 'Contact Us'],
  },
  {
    title: 'Resources',
    links: ['Online', 'Music', 'Counseling', 'Leaders Network', 'Podcasts', 'Store'],
  },
  {
    title: 'More',
    links: ['Give', 'Careers', 'News', 'Privacy', 'Terms', 'Investing'],
  },
]
</script>

<template>
  <div class="w-full bg-white text-black font-sans antialiased">

    <!-- ===== HERO SECTION ===== -->
    <section class="max-w-[1360px] mx-auto px-6 pt-24 pb-20 text-center">
      <h1 class="text-5xl md:text-7xl font-normal leading-tight">Contact Us</h1>
      <h4 class="mt-6 text-xl md:text-2xl font-normal text-gray-700">We'd love to hear from you!</h4>
    </section>

    <!-- ===== FORM + SIDEBAR SECTION ===== -->
    <section class="max-w-[1360px] mx-auto px-6 pb-24">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-10">

        <!-- LEFT: Contact Form -->
        <div>
          <h5 class="text-2xl font-normal mb-8">Send Us a Message</h5>

          <form @submit.prevent="submitForm" class="space-y-6" novalidate>
            <!-- Inquiry Type -->
            <div>
              <label class="block text-base font-normal mb-3">Inquiry Type</label>
              <select
                v-model="form.inquiryType"
                class="w-full bg-[#f3f3f3] border border-[#cccccc] px-3 py-2 text-sm h-[42px] focus:outline-none focus:border-black transition-colors"
              >
                <option value="" disabled>Select one...</option>
                <option v-for="type in inquiryTypes" :key="type" :value="type">{{ type }}</option>
              </select>
              <p v-if="errors.inquiryType" class="text-red-600 text-xs mt-1">{{ errors.inquiryType }}</p>
            </div>

            <!-- Name -->
            <div>
              <label class="block text-base font-normal mb-3">Your Name</label>
              <input
                v-model="form.name"
                type="text"
                class="w-full bg-[#f3f3f3] border border-[#cccccc] px-3 py-2 text-sm h-[42px] focus:outline-none focus:border-black transition-colors"
              />
              <p v-if="errors.name" class="text-red-600 text-xs mt-1">{{ errors.name }}</p>
            </div>

            <!-- Email -->
            <div>
              <label class="block text-base font-normal mb-3">Your Email</label>
              <input
                v-model="form.email"
                type="email"
                class="w-full bg-[#f3f3f3] border border-[#cccccc] px-3 py-2 text-sm h-[42px] focus:outline-none focus:border-black transition-colors"
              />
              <p v-if="errors.email" class="text-red-600 text-xs mt-1">{{ errors.email }}</p>
            </div>

            <!-- Subject -->
            <div>
              <label class="block text-base font-normal mb-3">Subject</label>
              <input
                v-model="form.subject"
                type="text"
                class="w-full bg-[#f3f3f3] border border-[#cccccc] px-3 py-2 text-sm h-[42px] focus:outline-none focus:border-black transition-colors"
              />
              <p v-if="errors.subject" class="text-red-600 text-xs mt-1">{{ errors.subject }}</p>
            </div>

            <!-- Message -->
            <div>
              <label class="block text-base font-normal mb-3">Message</label>
              <textarea
                v-model="form.message"
                rows="5"
                placeholder="How can we help?"
                class="w-full bg-[#f3f3f3] border border-[#cccccc] px-3 py-2 text-sm focus:outline-none focus:border-black transition-colors resize-y"
              ></textarea>
              <p v-if="errors.message" class="text-red-600 text-xs mt-1">{{ errors.message }}</p>
            </div>

            <!-- Submit -->
            <button
              type="submit"
              class="bg-black text-white text-lg px-6 py-2 hover:bg-gray-800 transition-colors"
            >
              Submit
            </button>

            <!-- Success message -->
            <p v-if="submitted" class="text-green-700 text-sm">
              Thank you! Your message has been sent. We'll get back to you shortly.
            </p>
          </form>
        </div>

        <!-- RIGHT: Sidebar -->
        <div class="space-y-12">
          <!-- Contact card -->
          <div>
            <h5 class="text-2xl font-normal mb-8">Contact Us</h5>
            <div class="space-y-6">
              <div>
                <p class="text-base text-gray-700 mb-1">Phone</p>
                <a :href="`tel:${phoneNumberTel}`" class="text-base text-black hover:text-gray-600 transition-colors">
                  {{ phoneNumber }}
                </a>
              </div>
              <div>
                <p class="text-base text-gray-700 mb-1">Email</p>
                <a :href="`mailto:${email}`" class="text-base text-black hover:text-gray-600 transition-colors break-all">
                  {{ email }}
                </a>
              </div>
              <div>
                <p class="text-base text-gray-700 mb-1">Office Hours</p>
                <p class="text-base">{{ officeHours }}</p>
              </div>
              <div>
                <p class="text-base text-gray-700 mb-1">Office Location</p>
                <p class="text-base" v-for="(line, i) in officeLocation" :key="i">{{ line }}</p>
              </div>
            </div>
          </div>

          <!-- Campus locations -->
          <div>
            <h5 class="text-2xl font-normal mb-4">Chapel Locations</h5>
            <p class="text-base text-gray-700 mb-3">Learn more about our chapels and offices.</p>
            <router-link to="/campuses" class="inline-flex items-center gap-2 text-base text-black underline hover:text-gray-600 transition-colors">
              View Chapels
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-3 h-3">
                <path d="M8.59 16.59 13.17 12 8.59 7.41 10 6l6 6-6 6z"/>
              </svg>
            </router-link>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== FAQ SECTION ===== -->
    <section class="max-w-[1360px] mx-auto px-6 py-24">
      <h3 class="text-3xl md:text-4xl font-medium uppercase tracking-wider mb-12 text-center">
        Frequently Asked Questions
      </h3>

      <div class="max-w-3xl mx-auto divide-y divide-gray-200 border-y border-gray-200">
        <div v-for="(faq, index) in faqs" :key="index">
          <button
            @click="toggleFaq(index)"
            class="w-full flex items-center justify-between py-5 text-left hover:bg-gray-50 transition-colors px-2"
            :aria-expanded="openFaq === index"
          >
            <span class="text-base md:text-lg font-normal pr-4">{{ faq.q }}</span>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              class="w-5 h-5 flex-shrink-0 transition-transform duration-300"
              :class="{ 'rotate-180': openFaq === index }"
            >
              <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
            </svg>
          </button>
          <div
            v-show="openFaq === index"
            class="pb-5 px-2 text-gray-700 text-base leading-relaxed"
          >
            {{ faq.a }}
          </div>
        </div>
      </div>
    </section>

    <!-- ===== STAY CONNECTED (dark band) ===== -->
    <section class="bg-[#1c1c1c] text-white py-20">
      <div class="max-w-[1360px] mx-auto px-6 text-center">
        <h2 class="text-3xl md:text-5xl font-normal mb-4">Stay Connected</h2>
        <h4 class="text-lg md:text-2xl font-normal text-white/70 mb-10">Follow along with what God is doing.</h4>

        <div class="flex items-center justify-center gap-6 flex-wrap">
          <a
            v-for="social in socials"
            :key="social.key"
            :href="social.url"
            target="_blank"
            rel="noopener noreferrer"
            :aria-label="social.name"
            class="text-white/80 hover:text-white hover:scale-110 transition-all duration-200"
          >
            <!-- Facebook -->
            <svg v-if="social.key === 'facebook'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6">
              <path d="M22 12.06C22 6.5 17.52 2 12 2S2 6.5 2 12.06c0 5 3.66 9.15 8.44 9.94v-7.03H7.9v-2.91h2.54V9.85c0-2.51 1.49-3.9 3.78-3.9 1.09 0 2.23.2 2.23.2v2.46h-1.26c-1.24 0-1.63.77-1.63 1.56v1.87h2.78l-.44 2.91h-2.34V22c4.78-.79 8.44-4.94 8.44-9.94z"/>
            </svg>
            <!-- WhatsApp -->
            <svg v-else-if="social.key === 'whatsapp'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6">
              <path d="M.057 24l1.687-6.163a11.867 11.867 0 01-1.587-5.946C.16 5.335 5.495 0 12.05 0a11.82 11.82 0 018.413 3.488 11.82 11.82 0 013.48 8.414c-.003 6.557-5.338 11.892-11.893 11.892a11.9 11.9 0 01-5.688-1.448L.057 24zm6.597-3.807c1.676.995 3.276 1.591 5.392 1.592 5.448 0 9.886-4.434 9.889-9.885.002-5.462-4.415-9.89-9.881-9.892-5.452 0-9.887 4.434-9.889 9.884a9.86 9.86 0 001.51 5.26l-.999 3.648 3.978-1.607zm11.387-5.464c-.074-.124-.272-.198-.57-.347-.297-.149-1.758-.868-2.031-.967-.272-.099-.47-.149-.669.149-.198.297-.768.967-.941 1.165-.173.198-.347.223-.644.074-.297-.149-1.255-.462-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.297-.347.446-.521.151-.172.2-.296.3-.495.099-.198.05-.372-.025-.521-.075-.148-.669-1.611-.916-2.206-.242-.579-.487-.501-.669-.51l-.57-.01c-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.71.306 1.263.489 1.694.626.712.226 1.36.194 1.872.118.571-.085 1.758-.719 2.006-1.413.248-.695.248-1.29.173-1.414z"/>
            </svg>
            <!-- YouTube -->
            <svg v-else-if="social.key === 'youtube'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6">
              <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/>
            </svg>
            <!-- Instagram -->
            <svg v-else-if="social.key === 'instagram'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6">
              <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163C8.741 0 8.332.014 7.052.072 2.695.272.273 2.69.073 7.052.014 8.332 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.332 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.668-.072-4.948-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.406-11.845a1.44 1.44 0 1 0 0 2.881 1.44 1.44 0 0 0 0-2.881z"/>
            </svg>
            <!-- TikTok -->
            <svg v-else-if="social.key === 'tiktok'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6">
              <path d="M12.525.02c1.31-.02 2.61-.01 3.91-.02.08 1.53.63 3.09 1.75 4.17 1.12 1.11 2.7 1.62 4.24 1.79v4.03c-1.44-.05-2.89-.35-4.2-.97-.57-.26-1.1-.59-1.62-.93-.01 2.92.01 5.84-.02 8.75-.08 1.4-.54 2.79-1.35 3.94-1.31 1.92-3.58 3.17-5.91 3.2-1.43.08-2.86-.31-4.08-1.03-2.02-1.19-3.44-3.37-3.57-5.72-.01-.37-.01-.74.01-1.11.16-2.06 1.27-4.01 2.95-5.19 1.45-1.04 3.29-1.5 5.07-1.21.02 1.48-.01 2.96.01 4.44-.82-.27-1.76-.18-2.49.33-.79.53-1.27 1.46-1.21 2.4.03 1.18.99 2.21 2.16 2.39.96.16 1.99-.34 2.51-1.17.16-.28.27-.59.27-.91.06-1.53.01-3.06.03-4.59.01-3.55-.01-7.1.02-10.65z"/>
            </svg>
          </a>
        </div>
      </div>
    </section>
  </div>
</template>