            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Sticky settings](/skyux/learn/develop/sticky-settings.md)
5.  [Integrations](/skyux/learn/develop/sticky-settings/integrations.md)

Custom components
=================

To save user configuration settings in custom components, use the `SkyUIConfigService` as illustrated in the following code sample. The `key` that you provide to the `UIConfigService` must be unique within your SPA.

TypeScript

Copy

    import {
      OnInit
    } from '@angular/core';
    import {
      SkyUIConfigService
    } from '@skyux/core';
    @Component({
      selector: 'app-custom-component',
      templateUrl: './custom.component.html'
    })
    export class CustomComponent implements OnInit {
      constructor(
        private configSvc: SkyUIConfigService
      ) { }
      public ngOnInit() {
        this.configSvc
          .getConfig(
            this.acceptedKey,
            this.acceptedValue
          )
          .subscribe(accepted => this.acceptedValue = accepted);
      }
      public saveChanges() {
        this.configSvc
          .setConfig(
            this.acceptedKey,
            this.acceptedValue
          );
      }
      private acceptedValue = {
        "value": false
      }	;
      private acceptedKey = 'agreement-accepted';
    }
  

    import {
      OnInit
    } from '@angular/core';
    import {
      SkyUIConfigService
    } from '@skyux/core';
    @Component({
      selector: 'app-custom-component',
      templateUrl: './custom.component.html'
    })
    export class CustomComponent implements OnInit {
      constructor(
        private configSvc: SkyUIConfigService
      ) { }
      public ngOnInit() {
        this.configSvc
          .getConfig(
            this.acceptedKey,
            this.acceptedValue
          )
          .subscribe(accepted => this.acceptedValue = accepted);
      }
      public saveChanges() {
        this.configSvc
          .setConfig(
            this.acceptedKey,
            this.acceptedValue
          );
      }
      private acceptedValue = {
        "value": false
      }  ;
      private acceptedKey = 'agreement-accepted';
    }