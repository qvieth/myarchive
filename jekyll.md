# jekyll

<iframe width="500" height="300" src="https://www.youtube.com/embed/iWowJBRMtpc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Getting Started With Jekyll, The Static Site Generator - codecourse](https://www.youtube.com/watch?v=iWowJBRMtpc&t=6s)

- dir
     - \_site
     - \_layouts
- front matter : powerful when come to templating engine
	- front matter variables declared 

---

- [step by step tutorial](https://jekyllrb.com/docs/step-by-step/01-setup/)
- take a look
     - https://jekyllrb.com/docs/configuration/markdown/
     - https://www.youtube.com/results?search_query=neuron+zettelkasten
- static site generator
- template + content
- [hugo vs jekyll](https://forestry.io/blog/hugo-and-jekyll-compared/)
     - hugo for big site - fast
     - shopify's liquid template vs hugo's go template
- [CSR vs SSR vs SSG](https://kirillibrahim.medium.com/gray-area-on-when-to-use-different-rendering-modes-csr-ssr-ssg-214a636a24a4)
     - csr : send blank page, client render | faster on server
     - ssr : send redered html better for seo | slower on server
     - ssg : like ssr but
          - render pages at **build time**
          - instead of **request time**
