---
component: 'media-query'
type: 'code-examples'
description: 'Code examples for the media-query component.'
---

# Media Query Code Examples

## Media query service with basic setup

**Component:** CoreMediaQueryBasicExampleComponent

**Selector:** `app-core-media-query-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import {
  SkyMediaQueryTestingController,
  provideSkyMediaQueryTesting,
} from '@skyux/core/testing';

import { CoreMediaQueryBasicExampleComponent } from './example.component';

describe('Media query example', () => {
  function setupTest(): {
    fixture: ComponentFixture<CoreMediaQueryBasicExampleComponent>;
    mediaController: SkyMediaQueryTestingController;
  } {
    const fixture = TestBed.createComponent(
      CoreMediaQueryBasicExampleComponent,
    );
    const mediaController = TestBed.inject(SkyMediaQueryTestingController);

    return { fixture, mediaController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      providers: [provideSkyMediaQueryTesting()],
    });
  });

  it('should change the breakpoint', () => {
    const { fixture, mediaController } = setupTest();

    const el = fixture.nativeElement as HTMLElement;

    mediaController.setBreakpoint('xs');
    fixture.detectChanges();

    expect(el.querySelector('.my-nav-mobile')).toBeTruthy();

    mediaController.setBreakpoint('lg');
    fixture.detectChanges();

    expect(el.querySelector('.my-nav-desktop')).toBeTruthy();
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { toSignal } from '@angular/core/rxjs-interop';
import { SkyMediaQueryService } from '@skyux/core';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Media query service with basic setup
 */
@Component({
  imports: [SkyIconModule],
  selector: 'app-core-media-query-basic-example',
  templateUrl: './example.component.html',
})
export class CoreMediaQueryBasicExampleComponent {
  protected breakpoint = toSignal(
    inject(SkyMediaQueryService).breakpointChange,
  );
}

```

#### example.component.html

```html
<p>Current media breakpoint: {{ breakpoint() }}</p>

@if (breakpoint() === 'xs') {
  <nav class="my-nav-mobile">
    <ul>
      <li>
        <button aria-label="Home" type="button">
          <sky-icon iconName="building" />
        </button>
      </li>
    </ul>
  </nav>
} @else {
  <nav class="my-nav-desktop">
    <ul>
      <li>
        <a href="#">Home</a>
      </li>
    </ul>
  </nav>
}

```

---

## Media query service using a responsive host container

**Component:** CoreMediaQueryResponsiveHostExampleComponent

**Selector:** `app-core-media-query-responsive-host-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### child.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { toSignal } from '@angular/core/rxjs-interop';
import { SkyMediaQueryService } from '@skyux/core';

@Component({
  selector: 'app-child',
  standalone: true,
  template: `<p>Breakpoint for child: {{ breakpoint() }}</p>`,
})
export class DemoChildComponent {
  protected breakpoint = toSignal(
    inject(SkyMediaQueryService).breakpointChange,
  );
}

```

#### container.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { toSignal } from '@angular/core/rxjs-interop';
import { SkyMediaQueryService, SkyResponsiveHostDirective } from '@skyux/core';

@Component({
  hostDirectives: [SkyResponsiveHostDirective],
  selector: 'app-container',
  standalone: true,
  styles: `
    :host {
      border: 1px solid var(--sky-border-color-neutral-medium-dark);
      display: block;
      margin: 0 auto;
      max-width: 800px;
    }
  `,
  template: `
    <p>Breakpoint within container: {{ breakpoint() }}</p>
    <ng-content />
  `,
})
export class DemoContainerComponent {
  protected breakpoint = toSignal(
    inject(SkyMediaQueryService).breakpointChange,
  );
}

```

#### example.component.spec.ts

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import {
  SkyMediaQueryTestingController,
  provideSkyMediaQueryTesting,
} from '@skyux/core/testing';

import { CoreMediaQueryResponsiveHostExampleComponent } from './example.component';

describe('Media query example', () => {
  function setupTest(): {
    fixture: ComponentFixture<CoreMediaQueryResponsiveHostExampleComponent>;
    mediaController: SkyMediaQueryTestingController;
  } {
    const fixture = TestBed.createComponent(
      CoreMediaQueryResponsiveHostExampleComponent,
    );
    const mediaController = TestBed.inject(SkyMediaQueryTestingController);

    return { fixture, mediaController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      providers: [provideSkyMediaQueryTesting()],
    });
  });

  it('should change the breakpoint', () => {
    const { fixture, mediaController } = setupTest();

    const el = fixture.nativeElement as HTMLElement;

    const containerWithHostDirective = el.querySelector<HTMLElement>(
      '[data-sky-id="container-w-host-directive"]',
    );

    const containerWithAttrDirective = el.querySelector<HTMLElement>(
      '[data-sky-id="container-w-attr"]',
    );

    mediaController.setBreakpoint('xs');
    fixture.detectChanges();

    expect(containerWithHostDirective).toHaveClass(
      'sky-responsive-container-xs',
    );
    expect(containerWithAttrDirective).toHaveClass(
      'sky-responsive-container-xs',
    );

    mediaController.setBreakpoint('lg');
    fixture.detectChanges();

    expect(containerWithHostDirective).toHaveClass(
      'sky-responsive-container-lg',
    );
    expect(containerWithAttrDirective).toHaveClass(
      'sky-responsive-container-lg',
    );
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, inject } from '@angular/core';
import { toSignal } from '@angular/core/rxjs-interop';
import { SkyMediaQueryService, SkyResponsiveHostDirective } from '@skyux/core';
import { SkyIconModule } from '@skyux/icon';

import { DemoChildComponent } from './child.component';
import { DemoContainerComponent } from './container.component';

/**
 * @title Media query service using a responsive host container
 */
@Component({
  imports: [
    CommonModule,
    DemoChildComponent,
    DemoContainerComponent,
    SkyResponsiveHostDirective,
    SkyIconModule,
  ],
  selector: 'app-core-media-query-responsive-host-example',
  styleUrl: './example.component.scss',
  templateUrl: './example.component.html',
})
export class CoreMediaQueryResponsiveHostExampleComponent {
  protected breakpoint = toSignal(
    inject(SkyMediaQueryService).breakpointChange,
  );
}

```

#### example.component.html

```html
<p>Viewport breakpoint: {{ breakpoint() }}</p>

<h4>Creating a responsive host using the host directive</h4>

<app-container data-sky-id="container-w-host-directive" />

<h4>Creating a responsive host using the directive attribute</h4>

<div
  #hostRef="skyResponsiveHost"
  class="my-container"
  data-sky-id="container-w-attr"
  skyResponsiveHost
>
  <p>Breakpoint within container: {{ hostRef.breakpointChange | async }}</p>
</div>

<h4>Creating a responsive host that wraps embedded views</h4>

<p>
  The responsive host's injector must be passed to the embedded view manually.
</p>

<app-container #responsiveHost="skyResponsiveHost">
  <ng-container
    [ngTemplateOutlet]="myTemplate"
    [ngTemplateOutletInjector]="responsiveHost.injector"
  />
</app-container>

<ng-template #myTemplate>
  <app-child />
</ng-template>

```

#### example.component.scss

```css
.my-container {
  border: 1px solid var(--sky-border-color-neutral-medium-dark);
  margin: 0 auto;
  max-width: 500px;
}

```

---