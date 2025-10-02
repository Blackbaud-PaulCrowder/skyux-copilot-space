---
component: 'date-pipe'
type: 'code-examples'
description: 'Code examples for the date-pipe component.'
---

# Date Pipe Code Examples

## Date pipe basic setup

**Component:** DatetimeDatePipeBasicExampleComponent

**Selector:** `app-datetime-date-pipe-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDatePipeModule } from '@skyux/datetime';

/**
 * @title Date pipe basic setup
 */
@Component({
  selector: 'app-datetime-date-pipe-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyDatePipeModule],
})
export class DatetimeDatePipeBasicExampleComponent {
  protected myDate = new Date('11/05/1955');
}

```

#### example.component.html

```html
<div>{{ myDate | skyDate }}</div>
<div>{{ myDate | skyDate: 'medium' }}</div>
<div>{{ myDate | skyDate: 'medium' : 'es-MX' }}</div>

```

---