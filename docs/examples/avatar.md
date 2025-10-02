---
component: 'avatar'
type: 'code-examples'
description: 'Code examples for the avatar component.'
---

# Avatar Code Examples

## Basic example

**Component:** AvatarExampleComponent

**Selector:** `app-avatar-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyAvatarHarness } from '@skyux/avatar/testing';

import { of } from 'rxjs';

import { AvatarExampleComponent } from './example.component';
import { DemoService } from './example.service';

describe('Basic avatar harness', () => {
  let uploadAvatarSpy: jasmine.Spy;

  beforeEach(() => {
    uploadAvatarSpy = jasmine
      .createSpy('uploadAvatarSpy')
      .and.returnValue(of(undefined));

    TestBed.configureTestingModule({
      providers: [
        {
          provide: DemoService,
          useValue: {
            uploadAvatar: uploadAvatarSpy,
          },
        },
      ],
    });
  });

  async function setupTest(): Promise<{
    fixture: ComponentFixture<AvatarExampleComponent>;
    harness: SkyAvatarHarness;
  }> {
    const fixture = TestBed.createComponent(AvatarExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const harness: SkyAvatarHarness = await loader.getHarness(
      SkyAvatarHarness.with({ dataSkyId: 'user-profile-avatar' }),
    );

    return { fixture, harness };
  }

  function createTestFile(fileSize: number): File {
    return new File(['a'.repeat(fileSize)], 'test.png', {
      type: 'image/png',
    });
  }

  it('should display the expected avatar image', async () => {
    const { harness } = await setupTest();

    await expectAsync(harness.getInitials()).toBeResolvedTo(undefined);
    await expectAsync(harness.getSrc()).toBeResolvedTo(
      'https://imgur.com/tBiGElW.png',
    );
  });

  it('should allow the user to change the avatar', async () => {
    const { harness } = await setupTest();

    await expectAsync(harness.getCanChange()).toBeResolvedTo(true);
  });

  it('should upload a new avatar and set the avatar src', async () => {
    const { harness } = await setupTest();

    const testFile = createTestFile(100);

    await harness.dropAvatarFile(testFile, true);

    expect(uploadAvatarSpy).toHaveBeenCalledOnceWith(testFile);

    await expectAsync(harness.getSrc()).toBeResolvedTo(jasmine.any(Blob));
  });

  it('should now allow files larger than 1,000 bytes', async () => {
    const { harness } = await setupTest();

    const maxFileSize = 1000;

    await harness.dropAvatarFile(createTestFile(maxFileSize));
    await expectAsync(harness.hasMaxSizeError()).toBeResolvedTo(false);

    await harness.dropAvatarFile(createTestFile(maxFileSize + 1));
    await expectAsync(harness.hasMaxSizeError()).toBeResolvedTo(true);

    await harness.closeError();
  });
});

```

#### example.component.ts

```typescript
import { Component, inject, signal } from '@angular/core';
import { SkyAvatarModule } from '@skyux/avatar';
import { SkyFileItem } from '@skyux/forms';

import { DemoService } from './example.service';

/**
 * @title Basic example
 */
@Component({
  selector: 'app-avatar-example',
  templateUrl: './example.component.html',
  imports: [SkyAvatarModule],
})
export class AvatarExampleComponent {
  #exampleSvc = inject(DemoService);

  protected readonly avatar = signal<string | File>(
    'https://imgur.com/tBiGElW.png',
  );
  protected readonly name = signal('Robert C. Hernandez');

  protected onAvatarChanged(fileItem: SkyFileItem): void {
    /**
     * This is where you might upload the new avatar,
     * but for this example we'll just update it locally.
     */
    if (fileItem) {
      this.#exampleSvc.uploadAvatar(fileItem.file).subscribe(() => {
        this.avatar.set(fileItem.file);
      });
    }
  }
}

```

#### example.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, delay, of } from 'rxjs';

@Injectable({
  providedIn: 'root',
})
export class DemoService {
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  public uploadAvatar(_file: File): Observable<void> {
    // Simulate uploading the file to a web service.
    return of(undefined).pipe(delay(500));
  }
}

```

#### example.component.html

```html
<sky-avatar
  data-sky-id="user-profile-avatar"
  [canChange]="true"
  [maxFileSize]="1000"
  [name]="name()"
  [src]="avatar()"
  (avatarChanged)="onAvatarChanged($event)"
/>

```

---