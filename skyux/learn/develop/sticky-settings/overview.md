            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Sticky settings](/skyux/learn/develop/sticky-settings.md)
5.  [Overview](/skyux/learn/develop/sticky-settings/overview.md)

Overview
========

Sticky settings save user preferences across sessions in data managers, flyouts, grids, and tile dashboards. Sticky settings preserve the [current data state of data managers](/skyux/components/data-manager.md), [width of flyouts](/skyux/components/flyout.md), the [column order and the sorting of columns in grids](/skyux/components/grid.md), and the [layout and collapsed state of tiles in tile dashboards](/skyux/components/tile.md).

To implement sticky settings, you must provide a class for `SkyUIConfigService` in your SPA's root module.

TypeScript

Copy

    import {
      AppUIConfigService
    }	 from './shared/services/app-ui-config.service';
    import {
      SkyUIConfigService
    }	 from '@skyux/core';
    @NgModule({
      providers: \[
        {
          provide: SkyUIConfigService,
          useClass: AppUIConfigService
        }
      \]
    })
    

    import {
      AppUIConfigService
    }   from './shared/services/app-ui-config.service';
    import {
      SkyUIConfigService
    }   from '@skyux/core';
    @NgModule({
      providers: [
        {
          provide: SkyUIConfigService,
          useClass: AppUIConfigService
        }
      ]
    })

Next, you implement a service to retrieve stored settings. The following example provides `AppUIConfigService` to utilize the [ngx-webstorage-service](https://github.com/dscheerens/ngx-webstorage-service). You could just as easily implement the service to call your backend if you store settings across devices.

TypeScript

Copy

      import {
        Injectable
      } from '@angular/core';
      import {
        LOCAL\_STORAGE,
        StorageService
      } from 'ngx-webstorage-service';
      import {
        SkyAppConfig
      } from '@skyux/config';
      @Injectable()
      export class AppUIConfigService {
        constructor(
          @Inject(LOCAL\_STORAGE) private storage: StorageService
          private config: SkyAppConfig
        ) {}
        public getConfig(key: string, defaultConfig: any): Observable<any> {
          key = this.buildSettingsKey(key);
          return of(
            this.storage.get(key) || defaultConfig;
          )
        }
        public setConfig(key: string, value: any): Observable<any> {
          key = this.buildSettingsKey(key);
          return of(
            this.storage.set(key, value)
          );
        }
        private buildSettingsKey(key: string): string {
          return \`skyux-spa-${this.config.runtime.app.name}-${key}\`;
        }
      }
    

    import {
      Injectable
    } from '@angular/core';
    import {
      LOCAL_STORAGE,
      StorageService
    } from 'ngx-webstorage-service';
    import {
      SkyAppConfig
    } from '@skyux/config';
    @Injectable()
    export class AppUIConfigService {
      constructor(
        @Inject(LOCAL_STORAGE) private storage: StorageService
        private config: SkyAppConfig
      ) {}
      public getConfig(key: string, defaultConfig: any): Observable<any> {
        key = this.buildSettingsKey(key);
        return of(
          this.storage.get(key) || defaultConfig;
        )
      }
      public setConfig(key: string, value: any): Observable<any> {
        key = this.buildSettingsKey(key);
        return of(
          this.storage.set(key, value)
        );
      }
      private buildSettingsKey(key: string): string {
        return `skyux-spa-${this.config.runtime.app.name}-${key}`;
      }
    }

The [data manager](/skyux/components/data-manager.md), [flyout](/skyux/components/flyout.md), [grid](/skyux/components/grid.md), and [tile](/skyux/components/tile.md) components support a `settingsKey` property for sticky settings. When you provide this property, the components automatically call the `SkyUIConfigService` stub to retrieve stored settings during appropriate actions. This is why you provide your own implementation as shown above.