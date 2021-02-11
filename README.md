# yoPostShopifyGraphQL
Posting to Shopfiy Via GraphQL

Usuage: 
``` typescript
const results = await postShopifyGraphQL(query);

```

``` typescript
import axios from 'axios';

export const postShopifyGraphQL = (query:any) => {
  return new Promise<any>((resolve, reject) => {
    axios({
      headers: {
        'X-Shopify-Access-Token': process.env.ACCESS_TOKEN,
        'Content-Type': 'application/json',
      },
      url: `https://${process.env.SHOP}.myshopify.com/admin/api/2019-10/graphql.json`,
      method: 'post',
      data: {
        query: query,
      },
    })
    .then(result => {
      resolve(result.data)
    }).catch(error => {
      reject(error)
    })
  });
}


