+++
title = "Effective Testing Strategies"
date = 2024-03-20
summary = "Build confidence in your code with a comprehensive testing approach"
tags = ["testing", "quality", "best-practices"]
categories = ["Development"]
+++

Good tests give you confidence to ship. Here's how to build an effective testing strategy.

## Testing Pyramid

Balance different types of tests:

- **Unit Tests** (70%) - Fast, isolated, many
- **Integration Tests** (20%) - Medium speed, combined components
- **E2E Tests** (10%) - Slow, full user flows, few

## Unit Testing

Test individual functions and components:

```javascript
// Function to test
function add(a, b) {
  return a + b;
}

// Test
describe('add', () => {
  it('adds two numbers correctly', () => {
    expect(add(2, 3)).toBe(5);
    expect(add(-1, 1)).toBe(0);
    expect(add(0, 0)).toBe(0);
  });
});
```

## Integration Testing

Test component interactions:

```javascript
describe('UserService', () => {
  it('creates user and sends welcome email', async () => {
    const user = await userService.createUser({
      email: 'test@example.com',
      name: 'Test User'
    });
    
    expect(user).toBeDefined();
    expect(emailService.sent).toHaveLength(1);
    expect(emailService.sent[0].to).toBe('test@example.com');
  });
});
```

## E2E Testing

Test complete user flows:

```javascript
describe('Login Flow', () => {
  it('allows user to login successfully', async () => {
    await page.goto('/login');
    await page.fill('[name=email]', 'user@example.com');
    await page.fill('[name=password]', 'password123');
    await page.click('button[type=submit]');
    
    await expect(page).toHaveURL('/dashboard');
    await expect(page.locator('.welcome')).toContainText('Welcome back');
  });
});
```

## Test Organization

Structure tests clearly:

```javascript
describe('Component/Feature', () => {
  describe('when condition', () => {
    it('does expected behavior', () => {
      // Arrange
      const input = setupTestData();
      
      // Act
      const result = performAction(input);
      
      // Assert
      expect(result).toEqual(expectedOutput);
    });
  });
});
```

## Mocking

Isolate units under test:

```javascript
// Mock external dependencies
jest.mock('./api', () => ({
  fetchUser: jest.fn()
}));

describe('UserProfile', () => {
  it('displays user data', async () => {
    // Setup mock
    fetchUser.mockResolvedValue({
      name: 'John Doe',
      email: 'john@example.com'
    });
    
    // Test component
    render(<UserProfile userId="123" />);
    
    await waitFor(() => {
      expect(screen.getByText('John Doe')).toBeInTheDocument();
    });
  });
});
```

## Test Coverage

Aim for meaningful coverage:

- 80%+ line coverage
- 100% critical path coverage
- Focus on business logic
- Don't test implementation details

```bash
# Generate coverage report
npm test -- --coverage

# Set coverage thresholds
{
  "jest": {
    "coverageThreshold": {
      "global": {
        "branches": 80,
        "functions": 80,
        "lines": 80,
        "statements": 80
      }
    }
  }
}
```

## Testing Best Practices

### Write Testable Code

```javascript
// Hard to test
function processOrder() {
  const data = fetch('/api/orders/123'); // Direct dependency
  const result = complex Processing(data);
  console.log(result); // Side effect
  return result;
}

// Easy to test
function processOrder(data, logger) { // Injected dependencies
  const result = complexProcessing(data);
  logger.log(result); // Injected logger
  return result;
}
```

### Test Behavior, Not Implementation

```javascript
// Bad - tests implementation
it('calls setState with new value', () => {
  wrapper.instance().setState = jest.fn();
  wrapper.find('button').simulate('click');
  expect(wrapper.instance().setState).toHaveBeenCalled();
});

// Good - tests behavior
it('increments counter when button clicked', () => {
  const { getByText, getByRole } = render(<Counter />);
  const button = getByRole('button');
  
  fireEvent.click(button);
  
  expect(getByText('Count: 1')).toBeInTheDocument();
});
```

### Keep Tests Fast

- Use in-memory databases
- Mock external services
- Parallelize test execution
- Skip slow tests in watch mode

### Test Edge Cases

```javascript
describe('divide', () => {
  it('handles normal cases', () => {
    expect(divide(10, 2)).toBe(5);
  });
  
  it('handles division by zero', () => {
    expect(() => divide(10, 0)).toThrow();
  });
  
  it('handles negative numbers', () => {
    expect(divide(-10, 2)).toBe(-5);
  });
  
  it('handles decimal results', () => {
    expect(divide(10, 3)).toBeCloseTo(3.33, 2);
  });
});
```

## CI/CD Integration

Run tests automatically:

```yaml
# GitHub Actions
name: Tests
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
      - run: npm ci
      - run: npm test
      - run: npm run test:e2e
```

Good tests are an investment. They catch bugs early, enable refactoring, and serve as documentation. Start simple and build your testing practice gradually.
