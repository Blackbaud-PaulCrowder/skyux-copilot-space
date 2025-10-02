---
component: 'navbar'
type: 'code-examples'
description: 'Code examples for the navbar component.'
---

# Navbar Code Examples

## Navbar with basic setup

**Component:** NavbarExampleComponent

**Selector:** `app-navbar-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideRouter } from '@angular/router';
import { SkyNavbarHarness } from '@skyux/navbar/testing';

import { NavbarExampleComponent } from './example.component';

describe('Basic navbar example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    navbarHarness: SkyNavbarHarness;
    fixture: ComponentFixture<NavbarExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [NavbarExampleComponent],
      providers: [provideRouter([])],
    }).compileComponents();

    const fixture = TestBed.createComponent(NavbarExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const navbarHarness: SkyNavbarHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyNavbarHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyNavbarHarness);

    return { navbarHarness, fixture };
  }

  it('should set up the navbar', async () => {
    const { navbarHarness, fixture } = await setupTest();

    const navbarItem1 = await navbarHarness.getItem({
      dataSkyId: 'navbar-item-1',
    });
    const navbarButton = await navbarItem1.querySelector('a');

    const clickSpy = spyOn(fixture.componentInstance, 'onItemClick');
    await navbarButton.click();
    expect(clickSpy).toHaveBeenCalledTimes(1);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { RouterModule } from '@angular/router';
import { SkyNavbarModule } from '@skyux/navbar';
import { SkyDropdownModule } from '@skyux/popovers';

/**
 * @title Navbar with basic setup
 */
@Component({
  selector: 'app-navbar-example',
  templateUrl: './example.component.html',
  imports: [RouterModule, SkyDropdownModule, SkyNavbarModule],
})
export class NavbarExampleComponent {
  public onItemClick(buttonText: string): void {
    alert(buttonText + ' button clicked!');
  }
}

```

#### example.component.html

```html
<sky-navbar data-sky-id="basic-navbar">
  <sky-navbar-item data-sky-id="navbar-item-1">
    <a
      routerLink="/"
      routerLinkActive="sky-navbar-item-active"
      (click)="onItemClick('Selected item')"
    >
      Selected item
    </a>
  </sky-navbar-item>
  <sky-navbar-item data-sky-id="navbar-item-2">
    <sky-dropdown>
      <sky-dropdown-button> Show dropdown </sky-dropdown-button>
      <sky-dropdown-menu>
        <sky-dropdown-item>
          <a routerLink="/" (click)="onItemClick('Item 1')"> Item 1 </a>
        </sky-dropdown-item>
        <sky-dropdown-item>
          <a routerLink="/" (click)="onItemClick('Item 2')"> Item 2 </a>
        </sky-dropdown-item>
        <sky-dropdown-item>
          <a routerLink="/" (click)="onItemClick('Item 3')"> Item 3 </a>
        </sky-dropdown-item>
      </sky-dropdown-menu>
    </sky-dropdown>
  </sky-navbar-item>
</sky-navbar>

```

---