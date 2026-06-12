<script setup lang="ts">
import type { HTMLAttributes } from "vue"
import { Primitive, type PrimitiveProps } from "reka-ui"
import { cva, type VariantProps } from "class-variance-authority"
import { cn } from "@/lib/utils"

type ButtonVariants = VariantProps<typeof buttonVariants>

const buttonVariants = cva(
    "group inline-flex items-center justify-center gap-1.5 shrink-0 whitespace-nowrap font-medium text-sm rounded-md cursor-pointer outline-none select-none transition-all disabled:pointer-events-none disabled:opacity-50 [&_svg]:pointer-events-none [&_svg:not([class*='size-'])]:size-4 [&_svg]:shrink-0 aria-invalid:ring-destructive/20 dark:aria-invalid:ring-destructive/40 aria-invalid:border-destructive",
    {
        variants: {
            variant: {
                default: "text-secondary-foreground bg-secondary hover:opacity-80",
                destructive:
                    "bg-destructive text-white hover:bg-destructive/90 focus-visible:ring-destructive/20 dark:focus-visible:ring-destructive/40 dark:bg-destructive/60",
                outline:
                    "border bg-background shadow-xs hover:bg-accent hover:text-accent-foreground dark:bg-input/30 dark:border-input dark:hover:bg-input/50",
                ghost: "hover:bg-accent hover:text-accent-foreground dark:hover:bg-accent/50",
                link: "text-primary underline-offset-4 hover:underline"
            },
            size: {
                default: "h-8.5 px-3 py-2.75",
                sm: "h-7.5 px-2.5 py-1.25",
                lg: "h-9.5 px-3 py-2",
                icon: "size-8.5",
                "icon-sm": "size-7.5",
                "icon-lg": "size-9.5"
            }
        },
        defaultVariants: {
            variant: "default",
            size: "default"
        }
    }
)

interface Props extends PrimitiveProps {
    variant?: ButtonVariants["variant"]
    size?: ButtonVariants["size"]
    class?: HTMLAttributes["class"]
}

const props = withDefaults(defineProps<Props>(), {
    as: "button"
})
</script>

<template>
    <Primitive
        data-slot="button"
        :data-variant="variant"
        :data-size="size"
        :as="as"
        :as-child="asChild"
        :class="cn(buttonVariants({ variant, size }), props.class)"
    >
        <slot />
    </Primitive>
</template>
