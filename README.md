# MESh

Stands for Megh's Emulated Shell. An extensible and responsive terminal-like personal / portfolio website built with SvelteKit. Has command executions, interactive mini-apps ("programs"), a virtual read-only filesystem, themes, an on-screen keyboard, internet radio streams and much more. Try to find the easter eggs ;)

Built and deployed on [GitHub Pages](https://megz15.github.io)

## Extending the Terminal

### Adding a New Command

1. Create a function in `src/lib/commands/yourCommand.ts`:
   ```ts
   export default function yourCommand(args: string[]): string {
     return "Hello from your new command!";
   }
   ```
2. Export and register the command in `src/lib/commands/allCommandsBarrel.ts`:
   ```ts
   yourCommand: {
     man: "Description of your command",
     cmd: yourCommand
   }
   ```

### Adding a New Program

1. Create a new route in `src/routes/yourProgram/+page.svelte`.
2. Add the program name to the `programs` array in `src/lib/system.svelte.ts`:
   ```ts
   export const programs: string[] = [
     // ...
     "yourProgram"
   ];
   ```
3. Launch your program from the terminal using `./yourProgram` or by going to http://localhost:5173/yourProgram.