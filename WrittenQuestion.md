# Written Section: Scaling the Global Feed

## Question

**What challenges might arise in serving the global article feed as traffic and data grow? What strategies would you use to ensure your backend and frontend continue to perform well under this load?**

---

## Answer

### Challenges

#### 1. **Frontend Performance & User Experience**

- Rendering hundreds of articles at once blocks the main thread which causes browser freeze and UI becomes unresponsive till the data is loaded.
- Bad Web Vitals scores (LCP, FID, CLS) which hurts search rankings.
- Large DOM size that causes high memory consumption.
- Poor mobile experience especially bad on low specs devices.
- Wasted bandwidth by re-downloading same data repeatedly, because current implementation does not use caching.

#### 2. **Database and API Performance**

- Response times increase from milliseconds to seconds.
- Querying huge amount of articles even with filters (tag, title, author, search keyword) becomes slow.
- Query problem when loading article details with eager fetching.
- Current in-memory database cannot handle large datasets.
- Data lose risk with in-memory database that means all data lost on server restart.

#### 3. **Server Specs Pressure**

- High memory usage due to in-memory database and lack of caching.
- CPU pressure from processing large result sets.
- Single server handling all read and write operations.
- No horizontal scaling strategy in current implementation.

---

## Strategies

### Backend Optimizations

- Making sure about having indexes to speed up the querying and sorting.
- Implementing pagination to avoid loading all articles at once.
- Implementing caching to avoid re-fetching unchanged data on navigation.
- Implementing horizontal scaling to distribute load across multiple servers.
- Implementing load balancing to distribute load across multiple servers.
- Implementing good monitoring to track the app performance.
- Moving to a scalable Database.

---

### Frontend Optimizations

- Implementing virtual scrolling.
- Enforce using OnPush change detection strategy.
- making sure about using `trackBy` function to avoid re-rendering unchanged items.
- Using proper state management (Shared state, components or services levels).
- Use memoized data selectors and caring about data mutation.
- Implementing lazy loading modules or splitting large components into smaller standalone components.
- Implementing any proper loading indicators like spinners or skelton loading.
- Implementing HTTP requests caching.
- Implementing optimistic UI updates with graceful error handling.
- Avoid memory leaks, like un-subscribing from observables and removing event listeners.
- Using good monitoring tools and measuring the web vitals consistently.
- After monitoring the system and knowing the UI bottleneck areas, revisiting the rendering patterns (the Long-term Option).

---
