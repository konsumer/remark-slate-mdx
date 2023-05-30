This will allow you to build a richtext editor for MDX, with slate & unified.

## Install

```
npm i remark-slate-mdx
```

## Usage

It's basically just a published version of [this](https://codesandbox.io/s/njvjyy), so see that for an example.


```js
import remarkSlate, { serialize } from 'remark-slate-mdx'

export const deserialize = (src) => {
  const { result } = unified()
    .use(remarkParse)
    .use(remarkMdx)
    .use(remarkSlate)
    .processSync(src)
  return result
}

const text = `
<Hero color='blue' cinnamon='/images/laydown-apps.svg' border='blue_thicko'>
  ## ABOUT GUMMICUBE

  # #1 ASO COMPANY IN THE WORLD


  Gummicube was founded in 2009 and has more than 11 years of experience in App Store Optimization and Mobile Marketing. We’ve contributed to the success of more Top 10 apps than anyone else in the world.

  Gummicube has one of the largest and most experienced teams in the world who have been trained in the fields of App Store Optimization, Conversion Rate Optimization, Paid Search, Mobile User Acquisition, Mobile Creative Development, Data Analytics, App Launch Strategies and more. We’ve worked across every category in each store with apps of all sizes and can deliver the experience and execution to win.

  <Button text="CONTACT US" />
</Hero>

<Content >
  <Block>
    #### Account Management

    Dedicated account managers with years of knowledge and experience
  </Block>
  <Block>
    #### Data Analytics

    Comprehensive analytics that examines all factors impacting performance
  </Block>
  <Block>
    #### Creative Analytics

    Award-winning design support with research backed by data & science
  </Block>
  <Block>
   #### User Acquisition

    Drive the best ROAS and user quality across all key marketing channels
  </Block>
</Content>

**Text**
`

const ast = deserialize(text)

// do soemthing with your slate editor with ast

// save the MDX content back in a database or whatever
console.log(serialize(ast))
```
