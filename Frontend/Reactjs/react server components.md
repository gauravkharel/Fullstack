from react con, this author made a framework for the RSC using JS

### the rules of the framework was
1. no bundler
2. no TS
3. no JSX transform
4. no optimization
5. no dependencies

### what we building
1. API: to fetch and render SC
2. Bundler: To bundle and render SC
3. router: to route on the client and fetch updated SC

The framework had this flow:
```
- Client
- renderToPipeableStream (fn)
- 1: {"name": App..}
- createFromFetch (fn)
- {type: "div", props: {...}}
- root.render
- <div>....
```

> Basically, RSC returns react element which is RSC Payload (found from nextjs docs) which gives framework instruction to return the HTML on the server
> Whereas, SSR returns static html
> But, both uses a server such as nodejs

