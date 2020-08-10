# Modules

## Operators
- `import`
  - input: module
  - output: reference to module's exports
- `export`
  - input: value to export
  - output: none

## Desired behavior
- Table that maps imports to references that point to corresponding export
- `import` sends control flow to imported module
  - if desired module is already in imports table simply return reference from that table
- once `export` is called, fork
  - thread1: staying in module until it finishes execution
  - thread2: returning to importing module's execution
  
## Support infastructure
- need a mutex to prevent importing same module twice
