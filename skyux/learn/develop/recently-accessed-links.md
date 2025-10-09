            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Recently accessed links](/skyux/learn/develop/recently-accessed-links.md)

Recently accessed links
=======================

Both the [sky-action-hub](/skyux/components/action-hub?docs-active-tab=development#class-skyactionhubcomponent.md) and the [sky-link-list-recently-accessed](/skyux/components/page?docs-active-tab=development#class-skypagelinkscomponent.md) components support displaying a list of recently accessed links.

Overview
--------

Some applications may want to display a list of recently accessed links to help users quickly navigate to frequently visited pages.

Configuration
-------------

To implement recently accessed links, you must provide an implementation of `SkyRecentlyAccessedService`.

TypeScript

Copy

    import {
      SkyRecentlyAccessedService
    } from '@skyux/router';
    
    import {
      CustomRecentlyAccessedService
    } from './shared/services/custom-recently-accessed.service';
    
    @NgModule({
      providers: [
        {
          provide: SkyRecentlyAccessedService,
          useClass: CustomRecentlyAccessedService
        }
      ]
    })
    export class AppModule { }

Next, you implement a service to push and retrieve recently accessed links:

TypeScript

Copy

    import {
      Injectable
    } from '@angular/core';
    
    import { Observable, of } from 'rxjs';
    
    import {
      SkyRecentlyAccessedAddLinkArgs,
      SkyRecentlyAccessedAddLinkResult,
      SkyRecentlyAccessedAddRouteArgs,
      SkyRecentlyAccessedGetLinksArgs,
      SkyRecentlyAccessedLinkList,
      SkyRecentlyAccessedService
    } from '@skyux/router';
    
    @Injectable()
    export class CustomRecentlyAccessedService extends SkyRecentlyAccessedService {
      public addRoute(
        _args: SkyRecentlyAccessedAddRouteArgs,
      ): Observable<SkyRecentlyAccessedAddLinkResult> {
        return of({ id: 'exampleId' });
      }
    
      public addLink(
        _args: SkyRecentlyAccessedAddLinkArgs,
      ): Observable<SkyRecentlyAccessedAddLinkResult> {
        return of({ id: 'exampleId' });
      }
    
      public abstract getLinks(
        _args: SkyRecentlyAccessedGetLinksArgs,
      ): Observable<SkyRecentlyAccessedLinkList> {
        return of([
          {
            label: 'My link',
            url: '/my-link',
            lastAccessed: new Date(2024, 2, 2),
          }
        ]);
      }
    }

Implementation
--------------

With the service in place, a small amount of code is needed to display the list of recently accessed links:

Copy

    <sky-link-list-recently-accessed
      [recentLinks]="{ requestedRoutes: [{ app:'example', route: '/opportunities' }] }"
    />

More complete code examples are available for both [sky-action-hub](/skyux/components/action-hub?docs-active-tab=code-examples.md) and [sky-link-list-recently-accessed](/skyux/components/page?docs-active-tab=code-examples.md) components.