```scss
.element {
	animation: fade-in-from-top 0.3s ease-in-out forwards;
	
	@for $i from 1 through 100 {
	  &:nth-child(#{$i}) {
		animation-delay: #{$i * .1}s;
	  }
	}
}

@keyframes fade-in-from-top {
  0% {
    opacity: 0;
    transform: translateY(-3rem);
  }

  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
```