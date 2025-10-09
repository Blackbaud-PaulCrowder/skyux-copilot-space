            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Sticky settings](/skyux/learn/develop/sticky-settings.md)
5.  [Testing](/skyux/learn/develop/sticky-settings/testing.md)

Testing
=======

To avoid external dependencies, either inject the default `SkyUIConfigService` in your `TestBed` configuration for unit tests or provide your own class to return fake data.

TypeScript

Copy

    TestBed.configureTestingModule({
      providers: \[
        {
          provide: SkyUIConfigService,
          useClass: SkyUIConfigService
        }
      \]
    });
    

    TestBed.configureTestingModule({
      providers: [
        {
          provide: SkyUIConfigService,
          useClass: SkyUIConfigService
        }
      ]
    });